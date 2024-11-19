# **Análise de Modelos de Previsão: SMOTE e Undersampling**

Este repositório avalia modelos de aprendizado de máquina para prever o risco de metástase hepática e/ou pulmonar em pacientes com câncer colorretal usando dados da base SEER. Dois métodos de balanceamento de dados foram implementados: **SMOTE (Synthetic Minority Oversampling Technique)** e **Undersampling**. A análise inclui métricas detalhadas de desempenho e visualizações das curvas ROC.

---

## **Técnicas de Balanceamento**

### **1. SMOTE (Synthetic Minority Oversampling Technique)**
- **O que é:** SMOTE é uma técnica de oversampling que cria novas amostras sintéticas para a classe minoritária ao invés de simplesmente replicar exemplos existentes. Ele utiliza a interpolação para gerar exemplos baseados nos vizinhos mais próximos de cada ponto da classe minoritária.
- **Como funciona:**
  1. Para cada exemplo da classe minoritária, o algoritmo seleciona \( k \) vizinhos mais próximos.
  2. Uma linha é criada no espaço de características entre o exemplo atual e um dos seus vizinhos.
  3. Um ponto aleatório é gerado ao longo dessa linha, criando uma nova amostra sintética.
- **Vantagens:**
  - Evita problemas de overfitting que podem ocorrer com técnicas de oversampling tradicionais (simples duplicação de amostras).
  - Preserva as relações entre os dados ao gerar novas amostras.
- **Relevância no Contexto:** Em problemas médicos, SMOTE é especialmente útil para lidar com o desbalanceamento em dados de diagnóstico, onde as classes minoritárias frequentemente representam condições críticas.

### **2. Undersampling**
- **O que é:** Undersampling reduz o número de exemplos da classe majoritária para equilibrar o conjunto de dados. Isso é feito removendo aleatoriamente amostras da classe maior.
- **Como funciona:**
  1. Amostras da classe majoritária são selecionadas aleatoriamente para serem removidas.
  2. O número de exemplos é reduzido até que o tamanho da classe majoritária seja equivalente (ou próximo) ao da classe minoritária.
- **Vantagens:**
  - Simplifica o problema ao reduzir a quantidade de dados a serem processados.
  - Pode melhorar o desempenho em modelos que são sensíveis ao tamanho do conjunto de dados.
- **Desvantagens:**
  - Risco de perda de informações valiosas devido à remoção de amostras.
  - Pode não capturar a complexidade da classe majoritária, resultando em menor desempenho em alguns casos.
- **Relevância no Contexto:** No cenário médico, undersampling pode ser usado quando há uma abundância de dados da classe majoritária (como pacientes saudáveis), permitindo um balanceamento mais eficiente para análise.

---

## **Descrição das Métricas de Avaliação**

### **1. Especificidade (Specificity)**
- **Definição:** Mede a capacidade do modelo de identificar corretamente os casos negativos (ou seja, pacientes sem metástase).
- **Relevância:** Importante em cenários médicos para evitar falsos positivos, que podem levar a tratamentos desnecessários.

### **2. Precisão (Precision)**
- **Definição:** Mede a proporção de previsões positivas corretas em relação ao total de previsões positivas.
- **Relevância:** Alta precisão indica que o modelo é confiável quando prediz um caso positivo.

### **3. Sensibilidade (Recall ou Sensitivity)**
- **Definição:** Mede a capacidade do modelo de identificar corretamente os casos positivos.
- **Relevância:** Essencial para garantir que a maioria dos casos positivos sejam detectados, especialmente em diagnósticos médicos.

### **4. F1-Score**
- **Definição:** Combina precisão e sensibilidade em uma única métrica harmônica.
- **Relevância:** Útil quando há um desbalanceamento entre classes, equilibrando os falsos positivos e negativos.

### **5. AUC-ROC (Area Under the Curve - Receiver Operating Characteristic)**
- **Definição:** Mede a capacidade do modelo de separar classes, baseado em uma curva de trade-off entre a taxa de verdadeiros positivos e a taxa de falsos positivos.
- **Relevância:** Quanto maior o AUC, melhor o modelo na distinção entre classes.

### **6. AUPR (Area Under the Precision-Recall Curve)**
- **Definição:** Mede a área sob a curva Precision-Recall.
- **Relevância:** Mais informativa que a AUC-ROC em cenários com classes desbalanceadas.

---

## **Como as Métricas se Relacionam**

### **1. Trade-offs entre Precision e Recall**
Precision e Recall têm uma relação de compromisso (trade-off). Melhorar a sensibilidade (Recall) geralmente aumenta os falsos positivos, reduzindo a precisão. Por outro lado, aumentar a precisão pode reduzir a sensibilidade, negligenciando casos positivos. 

### **2. F1-Score**
Combina Precision e Recall, criando um equilíbrio entre as duas métricas. É especialmente útil em cenários com desbalanceamento de classes.

### **3. AUC-ROC e AUPR**
Enquanto o AUC-ROC avalia a capacidade geral de separação do modelo, o AUPR é mais sensível ao desbalanceamento entre classes e foca na eficiência em identificar a classe minoritária.

### **4. Contexto Médico**
A especificidade ajuda a reduzir falsos positivos, enquanto o Recall é crucial para não perder casos positivos críticos.

---

## **Referências**

1. Saito, T., & Rehmsmeier, M. (2015). The precision-recall plot is more informative than the ROC plot when evaluating binary classifiers on imbalanced datasets. *PloS one, 10*(3), e0118432.  
2. Van Rijsbergen, C. J. (1979). Information Retrieval (2nd edition). Butterworth.  
3. Davis, J., & Goadrich, M. (2006). The relationship between Precision-Recall and ROC curves. *Proceedings of the 23rd international conference on Machine learning* (pp. 233-240).  
4. Powers, D. M. (2011). Evaluation: From Precision, Recall and F-Measure to ROC, Informedness, Markedness & Correlation. *Journal of Machine Learning Technologies*, 2(1), 37-63.
