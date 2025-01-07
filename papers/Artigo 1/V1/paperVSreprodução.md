# Comparação de Resultados: Artigo Original vs. Experimentos Reproduzidos

Esta análise apresenta uma comparação detalhada entre os resultados obtidos no artigo original e aqueles reproduzidos nos experimentos. A tabela a seguir destaca os valores de AUC (Área Sob a Curva ROC) para diferentes algoritmos de aprendizado de máquina sob cenários com oversampling (SMOTE) e undersampling, tanto para conjuntos de treino quanto de teste. Além disso, uma análise das causas prováveis das diferenças é fornecida.

## Tabela Comparativa de Resultados

```markdown
| Modelo            | AUC Artigo - Treino com SMOTE | AUC Experimento - Treino com SMOTE | AUC Artigo - Teste com SMOTE | AUC Experimento - Teste com SMOTE | AUC Artigo - Treino com Undersampling | AUC Experimento - Treino com Undersampling | AUC Artigo - Teste com Undersampling | AUC Experimento - Teste com Undersampling | Causas Prováveis                                                                                       |
|-------------------|--------------------------------|------------------------------------|------------------------------|------------------------------------|----------------------------------------|----------------------------------------|--------------------------------------|------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Random Forest     | 0.9562                         | 1.0000                             | 0.9562                       | 0.8733                             | 0.9868                                 | 1.0000                                 | 0.9868                               | 0.8775                                   | Overfitting no treino e diferença nos hiperparâmetros.                                                |
| Decision Tree     | 0.9205                         | 1.0000                             | 0.9205                       | 0.6769                             | 0.9878                                 | 1.0000                                 | 0.9878                               | 0.7090                                   | Overfitting no treino e alta sensibilidade a dados desbalanceados.                                    |
| SVM               | 0.8577                         | 0.9033                             | 0.8577                       | 0.8497                             | 0.8693                                 | 0.8715                                 | 0.8693                               | 0.8419                                   | Hiperparâmetros diferentes e implementação distinta.                                                  |
| Naive Bayes       | 0.8006                         | 0.7888                             | 0.8006                       | 0.7732                             | 0.7970                                 | 0.7783                                 | 0.7970                               | 0.7729                                   | Diferenças na divisão dos dados e possíveis variações no algoritmo.                                   |
| KNN               | 0.8901                         | 0.9873                             | 0.8901                       | 0.7804                             | 0.9321                                 | 0.9002                                 | 0.9321                               | 0.7923                                   | Diferença nos dados e possíveis erros no pré-processamento.                                           |
| XGBoost           | 0.8838                         | 0.9862                             | 0.8838                       | 0.8834                             | 0.9044                                 | 0.9600                                 | 0.9044                               | 0.8762                                   | Possíveis ajustes diferentes de hiperparâmetros.                                                      |
| Gradient Boosting | 0.8492                         | 0.9684                             | 0.8492                       | 0.8776                             | 0.8502                                 | 0.8907                                 | 0.8502                               | 0.8866                                   | Parâmetros ou técnicas de balanceamento distintas.                                                    |
```

## Gráficos

### Gráficos retirados do artigo


![artigo grafico](https://github.com/user-attachments/assets/35cafe49-36f2-4de5-a1ef-5cec6f038aca)


#### Gráficos realizados com a reprodução
![artigo grafico 2](https://github.com/user-attachments/assets/3be70ffd-4ce1-4620-8322-fa96c0ab9b06)



## Análise das Diferenças

### 1. Diferenças nos Dados
- **Particionamento dos Dados:** A divisão de dados em treino e teste pode ter introduzido variações. Mesmo seguindo o mesmo tamanho de divisão, a semente de aleatoriedade utilizada no artigo original pode não ter sido replicada.
- **Pré-processamento:** Pequenas diferenças no pré-processamento dos dados, como normalização ou codificação de variáveis categóricas, podem impactar os resultados.

### 2. Configuração dos Modelos
- **Hiperparâmetros:** Algoritmos como Random Forest e XGBoost dependem fortemente de hiperparâmetros (número de árvores, profundidade máxima, taxa de aprendizado, etc.). Caso os valores exatos não tenham sido especificados no artigo, as diferenças são esperadas.
- **Implementação da Biblioteca:** Variações entre versões de bibliotecas ou implementações de algoritmos podem levar a pequenas diferenças nos cálculos.

### 3. Oversampling e Undersampling
- **SMOTE:** Diferenças no comportamento do SMOTE podem ser causadas por parâmetros como o número de vizinhos usados para gerar dados sintéticos.
- **Variação nos Dados Sintéticos:** Os dados sintéticos gerados pelo SMOTE podem variar dependendo da ordem de execução e da semente aleatória usada.

### 4. Overfitting nos Conjuntos de Treino
Os valores de AUC=1.0 para Random Forest e Decision Tree no conjunto de treino indicam que esses modelos ajustaram excessivamente os dados no experimento reproduzido. Isso não foi observado no artigo original, o que sugere diferenças no controle do overfitting.

---

Essa análise detalhada pode ser usada para orientar ajustes no experimento e garantir maior alinhamento com os resultados do artigo original. Caso precise de ajuda para realizar algum ajuste específico, entre em contato!

