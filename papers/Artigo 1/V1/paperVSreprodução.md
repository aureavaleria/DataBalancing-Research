# Comparação de Resultados: Artigo Original vs. Experimentos Reproduzidos

A tabela abaixo apresenta uma comparação dos valores de AUC para diferentes algoritmos sob cenários com SMOTE e undersampling, tanto para treino quanto para teste. As diferenças são analisadas brevemente ao final.

---

## Gráficos

### Gráficos do Artigo Original
<img src="https://github.com/user-attachments/assets/4ef736c5-2af5-4d46-8c1c-e46d9318b846" alt="Descrição da imagem" style="width:700px; height:auto;">

### Gráficos dos Experimentos Reproduzidos
<img src="https://github.com/user-attachments/assets/1bb7b878-95e1-498a-a491-d36f0a4f4bac" alt="Descrição da imagem" style="width:700px; height:auto;">

### Análise de Resultados

- **Gráfico do Artigo Original**: Resultados consistentes entre as métricas (Accuracy, AUC, Precision, Recall e F1-score). Destaque para:
  - **Random Forest (RF)**: Maior AUC (0.956), indicando alta capacidade preditiva.
  - **KNN**: Alta Accuracy (0.852) e AUC (0.899), com boa precisão.
  - **Decision Tree (DT)**: Menor Recall, sugerindo dificuldades com classes menos representadas.

- **Gráfico dos Experimentos Reproduzidos**: Desempenhos inferiores ao artigo original, com destaque para:
  - **Random Forest**: Recall alto (0.808), mas Precision (0.392) e F1-score (0.528) reduzidos, sugerindo possível overfitting.
  - **Gradient Boosting**: Resultados mais equilibrados, porém inferiores ao esperado.
  - **Decision Tree**: Recall mais baixo (0.297), indicando dificuldades em detectar classes positivas.

---
## Tabelas de Comparação de desempenhos de previsão de diferentes modelos para sobreamostragem.

| Model           | Accuracy (Original) | AUC (Original) | Precision (Original) | Recall (Original) | F1-score (Original) | Accuracy (Reproduced) | AUC (Reproduced) | Precision (Reproduced) | Recall (Reproduced) | F1-score (Reproduced) |
|------------------|---------------------|----------------|-----------------------|-------------------|---------------------|-----------------------|------------------|-------------------------|---------------------|-----------------------|
| Random Forest    | 0.895               | 0.954          | 0.929                | 0.944            | 0.936              | 0.786                 | 0.878            | 0.392                  | 0.808              | 0.528                |
| Decision Tree    | 0.741               | 0.920          | 0.906                | 0.890            | 0.897              | 0.708                 | 0.709            | 0.297                  | 0.710              | 0.419                |
| SVM              | 0.785               | 0.857          | 0.771                | 0.807            | 0.788              | 0.754                 | 0.842            | 0.351                  | 0.786              | 0.485                |
| Naive Bayes      | 0.737               | 0.773          | 0.750                | 0.705            | 0.727              | 0.718                 | 0.773            | 0.273                  | 0.770              | 0.421                |
| KNN              | 0.852               | 0.890          | 0.818                | 0.902            | 0.819              | 0.713                 | 0.779            | 0.309                  | 0.758              | 0.439                |
| XGBoost          | 0.809               | 0.883          | 0.795                | 0.828            | 0.811              | 0.784                 | 0.856            | 0.386                  | 0.806              | 0.524                |
| Gradient Boosting| 0.773               | 0.849          | 0.774                | 0.774            | 0.772              | 0.795                 | 0.887            | 0.405                  | 0.817              | 0.541                |


### Análise Comparativa: Modelos de Previsão para Sobreamostragem

A tabela acima compara os desempenhos de diferentes modelos de aprendizado de máquina no contexto de sobreamostragem, avaliando métricas como Accuracy, AUC, Precision, Recall e F1-score entre os resultados originais e reproduzidos. Aqui está uma análise detalhada:

---

### 1. **Desempenho Geral**
   - **Random Forest (RF)**: No conjunto original, RF apresentou os melhores resultados gerais com um AUC de 0.954, indicando excelente separação de classes. Nos experimentos reproduzidos, houve uma significativa perda de desempenho nas métricas de precisão (Precision) e F1-score, com uma queda de mais de 50%. Isso sugere possível **overfitting** nos experimentos reproduzidos.
   - **Decision Tree (DT)**: O modelo original também teve desempenho satisfatório (AUC de 0.920 e F1-score de 0.897). Nos experimentos reproduzidos, houve uma forte redução no Precision (0.297), resultando em um F1-score reduzido (0.419), apontando para dificuldades em identificar classes minoritárias.
   - **Support Vector Machine (SVM)**: Apresenta desempenho equilibrado nos dados originais, com AUC de 0.857 e F1-score de 0.788. Na reprodução, o AUC (0.842) e o Recall (0.786) permaneceram estáveis, mas houve perda significativa em Precision, afetando negativamente o F1-score.
   - **Naive Bayes (NB)**: O modelo manteve resultados consistentes em AUC (0.773) e Recall (0.770) entre os cenários original e reproduzido. No entanto, Precision caiu para 0.273, prejudicando o F1-score.
   - **K-Nearest Neighbors (KNN)**: Demonstrou bom desempenho no conjunto original (Accuracy de 0.852 e AUC de 0.890), mas houve redução em todas as métricas no cenário reproduzido, especialmente Precision (0.309) e F1-score (0.439).
   - **XGBoost**: Consistiu em um dos modelos mais estáveis, com desempenho próximo entre os resultados originais (AUC de 0.883) e reproduzidos (AUC de 0.856). Apesar disso, o Precision caiu consideravelmente, resultando em menor F1-score nos dados reproduzidos.
   - **Gradient Boosting**: Apresentou os resultados mais equilibrados entre os modelos, com ligeira melhoria em AUC no cenário reproduzido (0.849 para 0.887). Embora Precision também tenha caído, o impacto no F1-score foi menos severo.

---

### 2. **Métricas de Desempenho Específicas**
   - **AUC**: O AUC no conjunto reproduzido foi consistentemente inferior ao original, indicando uma redução na capacidade geral dos modelos de distinguir entre classes. Esta queda foi mais acentuada em Random Forest (-0.076) e Decision Tree (-0.211).
   - **Precision**: Precision caiu drasticamente na maioria dos modelos reproduzidos, sugerindo que os experimentos sofreram com falsos positivos. Esta métrica foi especialmente crítica em Decision Tree (-0.609) e Naive Bayes (-0.477).
   - **Recall**: O Recall foi menos afetado em comparação à Precision, refletindo uma razoável capacidade de identificar a classe positiva. No entanto, houve quedas significativas em Random Forest e KNN.
   - **F1-Score**: Como métrica que equilibra Precision e Recall, o F1-score caiu em todos os modelos reproduzidos, com impacto mais significativo em Random Forest, Decision Tree e KNN.

---

### 3. **Modelos com Melhor Estabilidade**
   - **Gradient Boosting**: Apresentou a menor diferença geral entre os cenários original e reproduzido, sugerindo maior robustez frente a variações no pipeline de treinamento.
   - **XGBoost**: Embora tenha apresentado quedas, manteve boa estabilidade nas métricas principais (AUC, Recall e F1-score).



## O gráfico mostra a importância relativa das variáveis ​​no modelo de floresta aleatória.
<img src="https://github.com/user-attachments/assets/990c080c-66aa-46ff-b84d-10ad8e461fb1" alt="Descrição da imagem" style="width:400px; height:auto;">


### Tabela dos Experimentos Reproduzidos
<img src="https://github.com/user-attachments/assets/83380901-3c34-461e-9313-aabafa1062f7" alt="Descrição da imagem" style="width:400px; height:auto;">




## Análise Comparativa

## Gráfico Reproduzido

<img src="https://github.com/user-attachments/assets/26c9b5b2-207b-4896-a04b-8a949c39a0d5" alt="Descrição da imagem" style="width:700px; height:auto;">

## Gráfico original
<img src="https://github.com/user-attachments/assets/48a5cd9b-b69e-4cd9-b23d-8528b41d1b0e" alt="Descrição da imagem" style="width:700px; height:auto;">


### AUC em Curvas ROC

- **Original**: AUC alcançando 0.9127 para Random Forest, refletindo um desempenho superior.
- **Reproduzido**: Na base interna, o AUC é de 0.8814, apresentando ligeira perda. Para a base externa, o AUC é de 0.6111, indicando problemas de generalização do modelo.

### AUC em Precision-Recall Curve

- **Original**: Valores de 0.896 e 0.611 foram reportados para diferentes cenários.
- **Reproduzido**: Precision-Recall Curve para a base interna apresentou AUC de 0.6120, semelhante à parte C do original. Na base externa, o AUC é extremamente baixo (0.2494), sinalizando dificuldades.

### Comportamento das Curvas

- **Curvas ROC**: No gráfico original, as curvas ROC mostram alta separação entre classes, enquanto os reproduzidos exibem degradação de desempenho em ambientes externos.
- **Precision-Recall**: O gráfico reproduzido para a base externa tem precisão reduzida, indicando problemas no balanceamento ou na adequação do modelo.

## Diferenças Observadas

### Dados e Modelos

- **Particionamento e Pré-processamento**: Pequenas variações na divisão e manipulação dos dados podem causar diferenças.
- **Hiperparâmetros e Implementação**: Ajustes nos parâmetros e versões de bibliotecas influenciam os resultados.

### Overfitting

A **AUC=1.0** observada em Random Forest e Decision Tree para o conjunto de treino indica possível overfitting nos experimentos reproduzidos, sugerindo ajustes no controle do modelo.

Tabela do Artigo Original## Diferenças Observadas e Análise Comparativa


  ### Conclusão e Pontos de Melhoria

As diferenças nos resultados podem ser atribuídas a fatores como particionamento dos dados, configurações de hiperparâmetros e variações nas técnicas de balanceamento. Para melhorar, recomenda-se:
- Refinar os **hiperparâmetros** dos modelos.
- Revisar o **pipeline de pré-processamento** para maior aderência ao artigo original.
- Testar **técnicas de balanceamento híbridas** para avaliar seu impacto nos resultados.

Essa análise sugere a importância de ajustes cuidadosos para reproduzir com maior fidelidade os resultados do artigo original e explorar soluções mais robustas para os modelos.
