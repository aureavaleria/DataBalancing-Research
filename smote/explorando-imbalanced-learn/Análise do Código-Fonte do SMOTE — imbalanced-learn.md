# Análise do Código-Fonte do SMOTE — imbalanced-learn

Este documento resume e explica os principais pontos do arquivo `base.py`, onde está implementada a base do SMOTE e suas variantes no pacote [imbalanced-learn](https://imbalanced-learn.org/stable/).

---

## Estrutura do Código

O arquivo `base.py` implementa a classe base `BaseSMOTE` e as classes específicas para diferentes variantes do SMOTE:

- **BaseSMOTE:** Classe mãe, define funções comuns para todas as variantes do SMOTE.
- **SMOTE:** Implementação padrão do Synthetic Minority Over-sampling Technique.
- **SMOTENC:** Versão adaptada para conjuntos de dados com variáveis contínuas e categóricas.
- **SMOTEN:** Variante para bases puramente categóricas.

---

## Principais Elementos

### 1. Importações

O código utiliza vários módulos do NumPy, SciPy e scikit-learn, além de funções utilitárias do próprio pacote imbalanced-learn.

### 2. Classe `BaseSMOTE`

- Define métodos e parâmetros compartilhados (ex: `k_neighbors`, `random_state`).
- Função `_make_samples`: Gera amostras sintéticas por interpolação linear entre pontos reais e seus vizinhos mais próximos.
- Função `_generate_samples`: Realiza o cálculo dos novos pontos sintéticos, incluindo adaptações para casos especiais como BorderlineSMOTE.
- Função `_in_danger_noise`: Identifica exemplos "em perigo" ou "ruído", utilizados em variantes especializadas.

### 3. Classe `SMOTE`

- Implementação padrão do algoritmo SMOTE.
- Método `_fit_resample`: Para cada classe minoritária, encontra vizinhos, gera exemplos sintéticos e concatena ao dataset.
- Utiliza os métodos herdados de `BaseSMOTE` para geração dos exemplos.

### 4. Classe `SMOTENC`

- Extende o SMOTE para trabalhar com variáveis categóricas e contínuas.
- Codifica variáveis categóricas com OneHotEncoder, aplica o SMOTE nas variáveis contínuas e trata categorias ao final.
- Método `_fit_resample` adaptado para lidar com diferentes tipos de variáveis.

### 5. Classe `SMOTEN`

- Variante para bases com apenas variáveis categóricas.
- Utiliza OrdinalEncoder para codificação e Value Difference Metric para medir distâncias entre categorias.
- Gera novos exemplos sintéticos escolhendo a moda dos vizinhos mais próximos para cada categoria.

