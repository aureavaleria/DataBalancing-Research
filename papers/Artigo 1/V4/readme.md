# Comparação de Técnicas de Balanceamento de Dados

Este repositório contém notebooks que comparam diferentes técnicas de balanceamento de dados aplicadas a modelos de aprendizado de máquina. O objetivo é analisar a eficácia de cada técnica no tratamento de conjuntos de dados desbalanceados, com foco no impacto nas métricas de avaliação, como F1-Score, AUC-ROC e AUC-PR.

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

## Objetivo

O objetivo principal desta análise é comparar as técnicas de balanceamento quanto à sua capacidade de:
1. Melhorar as métricas de desempenho em modelos como Decision Tree, Random Forest, SVM, Naive Bayes, KNN, XGBoost e Gradient Boosting.
2. Identificar cenários em que cada técnica é mais eficaz, considerando datasets desbalanceados e os desafios relacionados.

