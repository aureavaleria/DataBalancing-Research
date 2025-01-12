# Comparação de Resultados: Artigo Original vs. Experimentos Reproduzidos

A tabela abaixo apresenta uma comparação dos valores de AUC para diferentes algoritmos sob cenários com SMOTE e undersampling, tanto para treino quanto para teste. As diferenças são analisadas brevemente ao final.

---

## Gráficos

### Gráficos do Artigo Original
<img src="https://github.com/user-attachments/assets/4ef736c5-2af5-4d46-8c1c-e46d9318b846" alt="Descrição da imagem" style="width:700px; height:auto;">

### Gráficos dos Experimentos Reproduzidos
<img src="https://github.com/user-attachments/assets/1bb7b878-95e1-498a-a491-d36f0a4f4bac" alt="Descrição da imagem" style="width:700px; height:auto;">

---
## Tabelas de Comparação de desempenhos de previsão de diferentes modelos para sobreamostragem.

| Model           | Accuracy (Original) | AUC (Original) | Precision (Original) | Recall (Original) | F1-score (Original) | Accuracy (Reproduced) | AUC (Reproduced) | Precision (Reproduced) | Recall (Reproduced) | F1-score (Reproduced) |
|------------------|---------------------|----------------|-----------------------|-------------------|---------------------|-----------------------|------------------|-------------------------|---------------------|-----------------------|
| SVM             | 0.785               | 0.857          | 0.771                | 0.807            | 0.788              | 0.754                 | 0.842            | 0.351                  | 0.786              | 0.485                |
| KNN             | 0.852               | 0.890          | 0.818                | 0.902            | 0.819              | 0.713                 | 0.779            | 0.309                  | 0.758              | 0.439                |
| DT              | 0.741               | 0.920          | 0.906                | 0.890            | 0.897              | NaN                   | NaN              | NaN                    | NaN                | NaN                  |
| NB              | 0.737               | 0.773          | 0.750                | 0.705            | 0.727              | NaN                   | NaN              | NaN                    | NaN                | NaN                  |
| RF              | 0.895               | 0.954          | 0.929                | 0.944            | 0.936              | NaN                   | NaN              | NaN                    | NaN                | NaN                  |
| XGBoost         | 0.809               | 0.883          | 0.795                | 0.828            | 0.811              | 0.784                 | 0.856            | 0.386                  | 0.806              | 0.524                |
| GBM             | 0.773               | 0.849          | 0.774                | 0.774            | 0.772              | 0.795                 | 0.887            | 0.405                  | 0.817              | 0.541                |
| Random Forest   | NaN                 | NaN            | NaN                  | NaN              | NaN                | 0.786                 | 0.878            | 0.392                  | 0.808              | 0.528                |
| Decision Tree   | NaN                 | NaN            | NaN                  | NaN              | NaN                | 0.708                 | 0.709            | 0.297                  | 0.710              | 0.419                |



## O gráfico mostra a importância relativa das variáveis ​​no modelo de floresta aleatória.
<img src="https://github.com/user-attachments/assets/990c080c-66aa-46ff-b84d-10ad8e461fb1" alt="Descrição da imagem" style="width:400px; height:auto;">


### Tabela dos Experimentos Reproduzidos
<img src="https://github.com/user-attachments/assets/83380901-3c34-461e-9313-aabafa1062f7" alt="Descrição da imagem" style="width:400px; height:auto;">

## Diferenças Observadas

### Dados e Modelos

- **Particionamento e Pré-processamento**: Pequenas variações na divisão e manipulação dos dados podem causar diferenças.
- **Hiperparâmetros e Implementação**: Ajustes nos parâmetros e versões de bibliotecas influenciam os resultados.

### Técnicas de Balanceamento

- **SMOTE**: Parâmetros como número de vizinhos podem causar divergências nos dados sintéticos.
- **Undersampling**: Amostras reduzidas podem exacerbar as diferenças.

### Overfitting

A **AUC=1.0** observada em Random Forest e Decision Tree para o conjunto de treino indica possível overfitting nos experimentos reproduzidos, sugerindo ajustes no controle do modelo.

Tabela do Artigo Original## Diferenças Observadas e Análise Comparativa

### Fatores Influenciadores

Pequenas variações no **particionamento e pré-processamento** dos dados, ajustes de **hiperparâmetros** e diferenças nas versões das bibliotecas utilizadas podem explicar as discrepâncias entre os resultados. Além disso, técnicas de balanceamento como **SMOTE** (afetado por parâmetros como número de vizinhos) e **undersampling** (que pode exacerbar diferenças em amostras reduzidas) impactaram diretamente os modelos. O **overfitting** observado nos experimentos reproduzidos, com AUC=1.0 em Random Forest e Decision Tree no conjunto de treino, destaca a necessidade de controle mais rigoroso nos modelos.

### Análise de Resultados

- **Tabela do Artigo Original**: Resultados consistentes entre as métricas (Accuracy, AUC, Precision, Recall e F1-score). Destaque para:
  - **Random Forest (RF)**: Maior AUC (0.956), indicando alta capacidade preditiva.
  - **KNN**: Alta Accuracy (0.852) e AUC (0.899), com boa precisão.
  - **Decision Tree (DT)**: Menor Recall, sugerindo dificuldades com classes menos representadas.

- **Tabela dos Experimentos Reproduzidos**: Desempenhos inferiores ao artigo original, com destaque para:
  - **Random Forest**: Recall alto (0.808), mas Precision (0.392) e F1-score (0.528) reduzidos, sugerindo possível overfitting.
  - **Gradient Boosting**: Resultados mais equilibrados, porém inferiores ao esperado.
  - **Decision Tree**: Recall mais baixo (0.297), indicando dificuldades em detectar classes positivas.

### Conclusão e Pontos de Melhoria

As diferenças nos resultados podem ser atribuídas a fatores como particionamento dos dados, configurações de hiperparâmetros e variações nas técnicas de balanceamento. Para melhorar, recomenda-se:
- Refinar os **hiperparâmetros** dos modelos.
- Revisar o **pipeline de pré-processamento** para maior aderência ao artigo original.
- Testar **técnicas de balanceamento híbridas** para avaliar seu impacto nos resultados.

Essa análise sugere a importância de ajustes cuidadosos para reproduzir com maior fidelidade os resultados do artigo original e explorar soluções mais robustas para os modelos.


<img src="https://github.com/user-attachments/assets/26c9b5b2-207b-4896-a04b-8a949c39a0d5" alt="Descrição da imagem" style="width:700px; height:auto;">


<img src="https://github.com/user-attachments/assets/48a5cd9b-b69e-4cd9-b23d-8528b41d1b0e" alt="Descrição da imagem" style="width:700px; height:auto;">


