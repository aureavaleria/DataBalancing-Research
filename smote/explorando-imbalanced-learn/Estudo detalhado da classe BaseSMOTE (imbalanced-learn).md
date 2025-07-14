# Estudo detalhado da classe BaseSMOTE (imbalanced-learn)
---

```python
class BaseSMOTE(BaseOverSampler):
    """
    Classe base para as diferentes variantes do SMOTE.

    Responsável por centralizar funções, parâmetros e lógica comum a todas as
    variantes do SMOTE presentes na biblioteca imbalanced-learn.
    """

    # Define restrições de tipos para parâmetros do construtor
    _parameter_constraints: dict = {
        **BaseOverSampler._parameter_constraints,
        "k_neighbors": [
            Interval(numbers.Integral, 1, None, closed="left"),  # número inteiro >= 1
            HasMethods(["kneighbors", "kneighbors_graph"]),      # ou objeto com métodos do kNN
        ],
    }

    def __init__(
        self,
        sampling_strategy="auto",    # Estratégia de balanceamento (ex: "auto" para igualar todas as classes)
        random_state=None,           # Semente de aleatoriedade (para reprodutibilidade)
        k_neighbors=5,               # Quantidade de vizinhos mais próximos
    ):
        # Inicializa a classe pai (BaseOverSampler)
        super().__init__(sampling_strategy=sampling_strategy)
        self.random_state = random_state
        self.k_neighbors = k_neighbors

    def _validate_estimator(self):
        """
        Checa/valida o estimador de vizinhos mais próximos (kNN),
        garantindo que está corretamente configurado para uso na geração dos exemplos sintéticos.
        """
        self.nn_k_ = check_neighbors_object(
            "k_neighbors", self.k_neighbors, additional_neighbor=1
        )

    def _make_samples(
        self, X, y_dtype, y_type, nn_data, nn_num, n_samples, step_size=1.0, y=None
    ):
        """
        Função auxiliar que retorna amostras sintéticas, construídas ao longo
        da linha que conecta amostras reais e seus vizinhos mais próximos.

        Parâmetros:
        - X: Dados base para gerar novos exemplos (array/matriz de features)
        - y_dtype: Tipo dos rótulos/classes
        - y_type: Valor da classe minoritária
        - nn_data: Base de dados dos vizinhos
        - nn_num: Índices dos vizinhos mais próximos
        - n_samples: Quantidade de amostras sintéticas a criar
        - step_size: Tamanho do passo para interpolação (padrão 1.0)
        - y: Rótulos verdadeiros dos vizinhos (usado em variantes)

        Retorna:
        - X_new: Novas amostras sintéticas (mesmo formato de X)
        - y_new: Rótulos das amostras sintéticas
        """

        # Inicializa gerador de aleatoriedade
        random_state = check_random_state(self.random_state)
        # Sorteia índices aleatórios para escolher pares base-vizinho
        samples_indices = random_state.randint(low=0, high=nn_num.size, size=n_samples)
        # Sorteia fatores de interpolação (gap), um para cada novo exemplo
        steps = step_size * random_state.uniform(size=n_samples)[:, np.newaxis]
        # Identifica o índice da amostra base e do vizinho correspondente
        rows = np.floor_divide(samples_indices, nn_num.shape[1])
        cols = np.mod(samples_indices, nn_num.shape[1])

        # Gera as novas amostras sintéticas de fato (usando interpolação)
        X_new = self._generate_samples(X, nn_data, nn_num, rows, cols, steps, y_type, y)
        # Cria os rótulos das amostras sintéticas (iguais à classe minoritária)
        y_new = np.full(n_samples, fill_value=y_type, dtype=y_dtype)
        return X_new, y_new

    def _generate_samples(
        self, X, nn_data, nn_num, rows, cols, steps, y_type=None, y=None
    ):
        r"""
        Realiza a geração dos exemplos sintéticos por interpolação.

        A regra é:
        s_s = s_i + gap * (s_nn - s_i)

        Onde:
        - s_s = novo exemplo sintético
        - s_i = amostra real base (da classe minoritária)
        - s_nn = vizinho mais próximo (da classe minoritária)
        - gap = valor aleatório entre 0 e 1

        Parâmetros e retorno similares ao método anterior.
        """

        # Calcula o vetor diferença entre base e vizinho escolhido
        diffs = nn_data[nn_num[rows, cols]] - X[rows]

        # Caso BorderlineSMOTE-2, pondera as diferenças se o vizinho for de classe diferente
        if y is not None:
            random_state = check_random_state(self.random_state)
            mask_pair_samples = y[nn_num[rows, cols]] != y_type
            diffs[mask_pair_samples] *= random_state.uniform(
                low=0.0, high=0.5, size=(mask_pair_samples.sum(), 1)
            )

        # Trata caso de matriz esparsa (sparse) ou densa (numpy array)
        if sparse.issparse(X):
            sparse_func = type(X).__name__
            steps = getattr(sparse, sparse_func)(steps)
            X_new = X[rows] + steps.multiply(diffs)
        else:
            X_new = X[rows] + steps * diffs

        return X_new.astype(X.dtype)

    def _in_danger_noise(self, nn_estimator, samples, target_class, y, kind="danger"):
        """
        Estima se um conjunto de amostras está em "perigo" (danger) ou é "ruído" (noise).

        Usado em variantes como BorderlineSMOTE e SVMSMOTE.

        - danger: maioria dos vizinhos são de classe diferente, mas não todos.
        - noise: todos os vizinhos são de classe diferente.

        Retorna um array booleano indicando amostras em perigo/ruído.
        """

        # Encontra os vizinhos (ignorando o próprio ponto)
        x = nn_estimator.kneighbors(samples, return_distance=False)[:, 1:]
        # Verifica quais vizinhos têm rótulo diferente da classe alvo
        nn_label = (y[x] != target_class).astype(int)
        # Conta quantos vizinhos são da classe majoritária
        n_maj = np.sum(nn_label, axis=1)

        if kind == "danger":
            # Em perigo: metade ou mais dos vizinhos são majoritários, mas não todos
            return np.bitwise_and(
                n_maj >= (nn_estimator.n_neighbors - 1) / 2,
                n_maj < nn_estimator.n_neighbors - 1,
            )
        else:  # kind == "noise":
            # Ruído: todos os vizinhos são da classe majoritária
            return n_maj == nn_estimator.n_neighbors - 1
