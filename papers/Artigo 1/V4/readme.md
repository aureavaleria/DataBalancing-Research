# Comparação de Técnicas de Balanceamento de Dados

Este repositório contém notebooks que comparam diferentes técnicas de balanceamento de dados aplicadas a modelos de aprendizado de máquina. O objetivo é analisar a eficácia de cada técnica no tratamento de conjuntos de dados desbalanceados, com foco no impacto nas métricas de avaliação, como F1-Score, AUC-ROC e AUC-PR.

## Biblioteca `imbalanced-learn`

A biblioteca **`imbalanced-learn`** é uma ferramenta poderosa para lidar com problemas de desbalanceamento em conjuntos de dados. Ela fornece diversas técnicas de pré-processamento que ajudam a equilibrar as classes antes de treinar modelos de aprendizado de máquina. As principais categorias de métodos disponíveis incluem:

- **Oversampling (Aumentar a classe minoritária):**
  - `SMOTE`: Gera amostras sintéticas interpolando vizinhos próximos.
  - `ADASYN`: Variante adaptativa do SMOTE que dá mais peso a amostras minoritárias mais difíceis de classificar.
  - `Borderline-SMOTE`: Focado em regiões próximas às fronteiras de decisão.

- **Undersampling (Reduzir a classe majoritária):**
  - `RandomUnderSampler`: Remove amostras da classe majoritária aleatoriamente.
  - `Tomek Links`: Remove amostras da classe majoritária próximas à classe minoritária.
  - `ClusterCentroids`: Reduz a classe majoritária utilizando centróides.

- **Combinações de Oversampling e Undersampling:**
  - `SMOTEENN`: Combina SMOTE com a técnica Edited Nearest Neighbors para remover ruídos.
  - `SMOTETomek`: Combina SMOTE com Tomek Links.

A biblioteca integra-se facilmente ao **scikit-learn**, permitindo uma implementação direta em pipelines. É uma ferramenta essencial para melhorar a performance de modelos treinados em datasets desbalanceados.

## Estrutura dos Arquivos

Cada arquivo representa uma técnica de balanceamento específica:

- **`Versão_4_(comparação_balanceamento_ADASYN).ipynb`**:
  Implementação e avaliação do método ADASYN, que adapta a geração de amostras sintéticas com base na complexidade local dos dados.

- **`Versão_4_(comparação_balanceamento_LOF_smote).ipynb`**:
  Combinação do SMOTE com o Fator de Outlier Local (LOF) para remover amostras sintéticas que podem ser ruídos, melhorando a representatividade da classe minoritária.

- **`Versão_4_(comparação_balanceamento_borderline).ipynb`**:
  Utilização do Borderline-SMOTE, focado em gerar amostras sintéticas próximas às fronteiras de decisão.

- **`Versão_4_(comparação_balanceamento_smote).ipynb`**:
  Implementação do SMOTE tradicional, que gera amostras sintéticas interpolando os vizinhos mais próximos.

- **`Versão_4_(comparação_balanceamento_smote_manual).ipynb`**:
  Implementação manual do SMOTE para melhor controle sobre os parâmetros e comportamento do método.

