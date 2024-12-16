## Versão 3: Ajustes de Hiperparâmetros

Nesta versão, realizamos o ajuste de hiperparâmetros dos principais algoritmos de aprendizado de máquina utilizados para prever o risco de metástase hepática e/ou pulmonar em pacientes com câncer colorretal (CRC) a partir da base de dados SEER.

### Modelos Implementados com Ajustes de Hiperparâmetros
Os hiperparâmetros foram ajustados utilizando técnicas como **Grid Search** e **Random Search**, validados com **Stratified K-Fold Cross-Validation (k=5)** para garantir uma avaliação robusta e consistente.

#### **1. Gradient Boosting**
- `n_estimators`: Número de árvores no modelo (ajustado para 100, 200, 300).
- `learning_rate`: Taxa de aprendizado (0.01, 0.05, 0.1).
- `max_depth`: Profundidade máxima de cada árvore (3, 5, 7).
- `subsample`: Fração das amostras usadas para treinar cada árvore (0.8, 1.0).
- `min_samples_split`: Número mínimo de amostras necessárias para dividir um nó (2, 5).

#### **2. Decision Tree**
- `criterion`: Função para medir a qualidade da divisão (`gini`, `entropy`).
- `max_depth`: Profundidade máxima da árvore (10, 20, 30).
- `min_samples_split`: Número mínimo de amostras necessárias para uma divisão (2, 5, 10).
- `min_samples_leaf`: Número mínimo de amostras por folha (1, 2, 5).

#### **3. Random Forest**
- `n_estimators`: Número de árvores no modelo (100, 200, 300).
- `criterion`: Função para medir a qualidade da divisão (`gini`, `entropy`).
- `max_depth`: Profundidade máxima das árvores (10, 20, 30).
- `min_samples_split`: Número mínimo de amostras para dividir um nó (2, 5).
- `min_samples_leaf`: Número mínimo de amostras em um nó folha (1, 2, 4).

#### **4. K-Nearest Neighbors (KNN)**
- `n_neighbors`: Número de vizinhos mais próximos (3, 5, 7, 9).
- `weights`: Método para ponderar os vizinhos (`uniform`, `distance`).
- `metric`: Métrica de distância (`euclidean`, `manhattan`, `minkowski`).

#### **5. XGBoost**
- `n_estimators`: Número de árvores no modelo (100, 200, 300).
- `learning_rate`: Taxa de aprendizado (0.01, 0.1, 0.2).
- `max_depth`: Profundidade máxima de cada árvore (3, 5, 7).
- `gamma`: Redução mínima de perda para dividir um nó (0, 0.1, 0.2).
- `colsample_bytree`: Fração de colunas a serem usadas por árvore (0.8, 1.0).

#### **6. Support Vector Machine (SVM)**
- `C`: Parâmetro de regularização (0.1, 1, 10, 100).
- `kernel`: Tipo de kernel usado no modelo (`linear`, `rbf`, `poly`).
- `gamma`: Coeficiente do kernel para `rbf` e `poly` (`scale`, `auto`, valores específicos como 0.01, 0.1).
- `degree`: Grau do polinômio para o kernel `poly` (3, 4, 5).

---

### Objetivo da Versão 3
O objetivo principal desta versão é otimizar os hiperparâmetros dos modelos para maximizar o desempenho na previsão de metástases. Todas as configurações foram validadas com **Stratified K-Fold Cross-Validation (k=5)**.

---

### Estrutura dos Arquivos
- **Versão_3_(ajustes_de_hiperparâmetros_Gradient_Boost)**: Ajuste de hiperparâmetros do Gradient Boosting.
- **Versão_3_(ajustes_de_hiperparâmetros_DT_RF)**: Ajuste de hiperparâmetros para Decision Tree e Random Forest.
- **Versão_3_(ajustes_de_hiperparâmetros_KNN)**: Ajuste de hiperparâmetros do K-Nearest Neighbors.
- **Versão_3_(ajustes_de_hiperparâmetros_XGBoost)**: Ajuste de hiperparâmetros do XGBoost.
- **Versão_3_(ajustes_de_hiperparâmetros_SVM)**: Ajuste de hiperparâmetros do Support Vector Machine.

---

### Próximos Passos
1. Comparar os resultados entre os modelos ajustados.
2. Selecionar o melhor modelo com base no desempenho das métricas.
3. Documentar o pipeline completo e gerar gráficos comparativos.

