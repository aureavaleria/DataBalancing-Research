# Machine Learning for Predicting Liver and/or Lung Metastasis in Colorectal Cancer

Este repositório contém o código para a reprodução do estudo **"Machine learning for predicting liver and/or lung metastasis in colorectal cancer: A retrospective study based on the SEER database"**. O objetivo deste trabalho é desenvolver modelos de aprendizado de máquina para prever a presença de metástases hepáticas e/ou pulmonares em pacientes com câncer colorretal (CRC). Utilizando dados da base SEER, o estudo abrange aproximadamente 53.000 pacientes diagnosticados entre 2010 e 2015. Foram explorados sete algoritmos de aprendizado de máquina: **Decision Tree, Random Forest, Naive Bayes, KNN, XGBoost, Gradient Boosting e SVM**.

## Estrutura do Código

### Parte 1: Importação de Bibliotecas e Preparação do Dataset
- Importação de bibliotecas essenciais para análise de dados, visualização e modelagem.
- Carregamento do dataset e tratamento de valores ausentes.
- Definição de variáveis preditoras (`X`) e variáveis alvo (`y`).

### Parte 2: Pré-processamento
- Codificação de variáveis categóricas com `LabelEncoder`.
- Combinação de variáveis alvo para criar uma coluna binária representando a presença de metástases.

### Parte 3: Configuração de Modelos e Validação Cruzada
- Configuração de sete modelos de aprendizado de máquina com hiperparâmetros ajustados.
- Implementação de validação cruzada estratificada com 5 folds (`StratifiedKFold`) para garantir uma avaliação robusta dos modelos, preservando a distribuição das classes em cada fold.

### Parte 4: Avaliação e Comparação de Modelos
- Aplicação de técnicas de balanceamento (`SMOTE`) no conjunto de treinamento para lidar com o desbalanceamento de classes.
- Escalonamento de dados com `StandardScaler`.
- Treinamento e validação de modelos em cada fold.
- Cálculo de métricas como precisão, recall, F1-Score, especificidade, AUC-ROC e AUPR, tanto nos conjuntos de treino quanto de teste.
- Geração de visualizações como matrizes de confusão, curvas ROC e Precisão-Recall.
- Compilação de métricas médias de todos os folds para análise comparativa.

## Validação Cruzada com k-fold
A técnica de validação cruzada k-fold foi utilizada para avaliar os modelos de forma consistente e minimizar a variabilidade nos resultados. Neste estudo:
- O dataset foi dividido em **5 folds estratificados**, preservando a proporção de classes em cada fold.
- Em cada iteração, **4 folds foram usados para treinamento e 1 fold para validação**.
- A validação cruzada garante que todos os dados sejam utilizados tanto para treinamento quanto para validação, proporcionando uma avaliação mais confiável do desempenho dos modelos.

## Resultados Esperados
Os resultados incluem a comparação das métricas de desempenho entre os modelos, permitindo identificar o algoritmo mais eficaz para prever metástases em pacientes com CRC. Além disso, os impactos do balanceamento de dados no desempenho dos modelos são analisados detalhadamente.

