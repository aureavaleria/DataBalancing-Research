# Resumo Teórico — SMOTE (Synthetic Minority Over-sampling Technique)

## O que é o SMOTE?

O SMOTE (Synthetic Minority Over-sampling Technique) é uma técnica de oversampling desenvolvida para corrigir o desbalanceamento de classes em conjuntos de dados, especialmente para problemas de classificação, onde uma das classes possui muito menos exemplos do que as outras.

Em vez de simplesmente duplicar exemplos da classe minoritária, o SMOTE **cria exemplos sintéticos** baseados na combinação de exemplos reais já existentes.

---

## Como o SMOTE funciona?
<img src="./Imagens/processo smote.png" width="400"/>


4. **Repetição do processo:**  
   Esse procedimento é repetido até que o número desejado de exemplos sintéticos seja criado, equilibrando assim a quantidade de exemplos entre as classes.

---

## Vantagens do SMOTE

- **Evita overfitting causado por simples replicação:**  
  Como cria exemplos novos, o modelo aprende uma região maior do espaço da classe minoritária.
- **Expande a fronteira de decisão da classe minoritária:**  
  Ajuda o classificador a distinguir melhor entre as classes.
- **Simples de implementar:**  
  E está disponível em diversas bibliotecas de machine learning.

---

## Limitações do SMOTE

- **Geração de ruído:**  
  Pode criar exemplos sintéticos em regiões próximas à classe majoritária, gerando confusão entre as classes (overlapping).
- **Sensível a outliers:**  
  Pode gerar exemplos sintéticos a partir de exemplos minoritários atípicos (outliers), aumentando ruído.
- **Não trata variáveis categóricas:**  
  O SMOTE padrão só funciona bem com variáveis numéricas contínuas.

---

## Principais Variantes do SMOTE

- **BorderlineSMOTE:**  
  Gera exemplos sintéticos apenas próximos da fronteira entre classes, onde a chance de erro é maior.

- **SMOTENC:**  
  Adaptação para tratar variáveis categóricas e numéricas ao mesmo tempo.

- **ADASYN:**  
  Foca em criar exemplos sintéticos onde a classe minoritária é mais difícil de aprender (regiões de maior erro).

- **KMeansSMOTE:**  
  Usa clustering (agrupamento) para gerar exemplos sintéticos em regiões mais densas da classe minoritária.

- **SMOTEENN e SMOTETomek:**  
  Combina SMOTE com técnicas de limpeza de dados (remoção de ruído) após o oversampling.

---

## Visualização Intuitiva

![smote](https://github.com/user-attachments/assets/2e75e868-8e7e-49c7-a271-b3672db8e03b)


As bolinhas vermelhas (classe minoritária) estão agrupadas e as azul (classe majoritária) são maioria. O SMOTE, em vez de só duplicar as bolinhas azuis, desenha novas bolinhas entre as existentes, **criando exemplos intermediários** para “preencher” a região minoritária.

---

## Quando usar SMOTE?

- Quando seu conjunto de dados tem **muito mais exemplos de uma classe do que de outra**.
- Quando modelos tradicionais apresentam baixo recall/sensibilidade na classe minoritária.
- Antes de treinar classificadores em problemas de saúde, fraudes, diagnósticos, etc., onde o desbalanceamento é frequente.

---

## Referências para aprofundar

- Chawla, N. V., et al. (2002). SMOTE: Synthetic Minority Over-sampling Technique. *Journal of Artificial Intelligence Research*.
- [imbalanced-learn documentation](https://imbalanced-learn.org/stable/over_sampling.html#smote-variants)
- He, H., & Garcia, E. (2009). Learning from Imbalanced Data. *IEEE TKDE*.



