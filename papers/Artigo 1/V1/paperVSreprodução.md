# Comparação de Resultados: Artigo Original vs. Experimentos Reproduzidos

A tabela abaixo apresenta uma comparação dos valores de AUC para diferentes algoritmos sob cenários com SMOTE e undersampling, tanto para treino quanto para teste. As diferenças são analisadas brevemente ao final.

## Tabela Comparativa de Resultados

| Modelo            | AUC Artigo - Treino SMOTE | AUC Experimento - Treino SMOTE | AUC Artigo - Teste SMOTE | AUC Experimento - Teste SMOTE | AUC Artigo - Treino Under | AUC Experimento - Treino Under | AUC Artigo - Teste Under | AUC Experimento - Teste Under | Causas Prováveis                       |
|-------------------|---------------------------|--------------------------------|--------------------------|--------------------------------|----------------------------|--------------------------------|--------------------------|--------------------------------|---------------------------------------|
| Random Forest     | 0.9562                    | 1.0000                         | 0.9562                   | 0.8733                         | 0.9868                     | 1.0000                         | 0.9868                   | 0.8775                         | Overfitting e ajustes de parâmetros. |
| Decision Tree     | 0.9205                    | 1.0000                         | 0.9205                   | 0.6769                         | 0.9878                     | 1.0000                         | 0.9878                   | 0.7090                         | Alta sensibilidade aos dados.        |
| SVM               | 0.8577                    | 0.9033                         | 0.8577                   | 0.8497                         | 0.8693                     | 0.8715                         | 0.8693                   | 0.8419                         | Configuração e implementação.        |
| Naive Bayes       | 0.8006                    | 0.7888                         | 0.8006                   | 0.7732                         | 0.7970                     | 0.7783                         | 0.7970                   | 0.7729                         | Divisão e variação nos dados.        |
| KNN               | 0.8901                    | 0.9873                         | 0.8901                   | 0.7804                         | 0.9321                     | 0.9002                         | 0.9321                   | 0.7923                         | Diferenças no pré-processamento.     |
| XGBoost           | 0.8838                    | 0.9862                         | 0.8838                   | 0.8834                         | 0.9044                     | 0.9600                         | 0.9044                   | 0.8762                         | Ajustes de hiperparâmetros.          |
| Gradient Boosting | 0.8492                    | 0.9684                         | 0.8492                   | 0.8776                         | 0.8502                     | 0.8907                         | 0.8502                   | 0.8866                         | Técnicas distintas de balanceamento. |

---

## Gráficos

### Gráficos do Artigo Original
![artigo grafico](https://github.com/user-attachments/assets/4ef736c5-2af5-4d46-8c1c-e46d9318b846)

### Gráficos dos Experimentos Reproduzidos
![artigo grafico 2](https://github.com/user-attachments/assets/1bb7b878-95e1-498a-a491-d36f0a4f4bac)
---
## Tabelas de Comparação de desempenhos de previsão de diferentes modelos para sobreamostragem.

### Tabela do Artigo Original
![tabela originaal](https://github.com/user-attachments/assets/bf5659c5-f596-43a7-97a4-7e31ea84a79c)

### Tabela dos Experimentos Reproduzidos
![tabela](https://github.com/user-attachments/assets/40a1537a-caaa-4f67-b1e1-3600843e2866)

## O gráfico mostra a importância relativa das variáveis ​​no modelo de floresta aleatória.
![rf-variavel original](https://github.com/user-attachments/assets/990c080c-66aa-46ff-b84d-10ad8e461fb1)

### Tabela dos Experimentos Reproduzidos
![rf-variavel reprodução](https://github.com/user-attachments/assets/83380901-3c34-461e-9313-aabafa1062f7)
