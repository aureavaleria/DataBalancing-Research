# Comparação de Variáveis: Base SEER do Artigo vs. Reprodução

Esta análise compara as distribuições de variáveis-chave da base de dados SEER, conforme descrito no artigo, com os valores observados na sua reprodução. A avaliação considera diferenças relevantes nas proporções e na frequência absoluta.

---

## Distribuição por Faixa Etária

| Faixa Etária       | Proporção (%) Artigo | Proporção (%) Reprodução | Diferença (%) |
|--------------------|----------------------|---------------------------|---------------|
| 65-69 years        | **14.2**            | 12.5                     | -1.7          |
| 60-64 years        | **13.8**            | 12.0                     | -1.8          |
| 70-74 years        | **12.8**            | 11.8                     | -1.0          |
| 75-79 years        | **12.0**            | 11.2                     | -0.8          |
| 85+ years          | **11.0**            | 11.1                     | +0.1          |

### Observação
Diferenças menores do que 2% foram observadas na maioria das faixas etárias, o que pode estar relacionado ao particionamento dos dados.

---

## Distribuição por Sexo

| Sexo    | Proporção (%) Artigo | Proporção (%) Reprodução | Diferença (%) |
|---------|----------------------|---------------------------|---------------|
| Male    | **53.0**            | 52.8                     | -0.2          |
| Female  | **47.0**            | 47.2                     | +0.2          |

### Observação
As proporções de gênero são praticamente idênticas entre o artigo e a reprodução.

---

## Distribuição por Raça

| Raça                                      | Proporção (%) Artigo | Proporção (%) Reprodução | Diferença (%) |
|------------------------------------------|----------------------|---------------------------|---------------|
| White                                    | **77.5**            | 77.7                     | +0.2          |
| Other (American Indian/AK Native, Asian) | **13.1**            | 12.9                     | -0.2          |
| Black                                    | **9.0**             | 9.0                      | 0.0           |
| Unknown                                  | **0.4**             | 0.4                      | 0.0           |

### Observação
A distribuição por raça também apresenta forte consistência entre o artigo e a reprodução.

---

## Distribuição de Estágios (Derived AJCC T, 7th ed)

| Estágio | Proporção (%) Artigo | Proporção (%) Reprodução | Diferença (%) |
|---------|----------------------|---------------------------|---------------|
| T3      | **44.0**            | 43.9                     | -0.1          |
| T1      | **18.6**            | 18.7                     | +0.1          |
| T2      | **12.1**            | 12.2                     | +0.1          |
| T4a     | **8.4**             | 8.4                      | 0.0           |

### Observação
Não foram identificadas diferenças significativas para os estágios do tumor.

---

## Comparação de Matrizes de Correlação: Artigo Original vs. Reprodução

Abaixo apresentamos as matrizes de correlação para os diferentes métodos de balanceamento (undersampling e SMOTE) utilizadas no artigo original e em nossa reprodução. As imagens em **tons roxos** referem-se aos gráficos apresentados no **artigo original**, enquanto as imagens em **tons azuis** são as matrizes geradas a partir da **reprodução** com base nas instruções fornecidas no artigo. Esta análise permite comparar o recorte realizado no estudo original com os resultados obtidos em nossa reprodução.

---

### Matriz de Correlação - Undersampling (Artigo Original)

<img src="https://github.com/user-attachments/assets/f5419f04-8c69-406e-9b73-83449e115f9f" alt="matriz correlação undersampling artigo" style="width:600px; height:auto;">

Nesta matriz observa-se a correlação entre variáveis do dataset com aplicação de undersampling, como descrito no artigo original. Variáveis como **Histologic Type ICD-O-3** e **ICD-O-3 Hist/behavior** apresentam alta correlação esperada.

---

### Matriz de Correlação - Undersampling (Reprodução)

<img src="https://github.com/user-attachments/assets/d52029c3-6173-4f68-96c5-4705e07ace35" alt="matriz correlação undersampling" style="width:600px; height:auto;">

A matriz gerada pela reprodução apresenta padrões semelhantes, com pequenas variações na correlação entre a variável alvo e variáveis como **Tumor Deposits**.

---

### Matriz de Correlação - SMOTE (Artigo Original)

<img src="https://github.com/user-attachments/assets/6910da25-f803-437b-b392-fab0884bc44b" alt="matriz correlação smote artigo" style="width:600px; height:auto;">

Com o uso de SMOTE, a matriz do artigo fortalece relações com a variável alvo, como entre **Tumor Deposits** e **Liver and/or Lung Metastasis**.

---

### Matriz de Correlação - SMOTE (Reprodução)

<img src="https://github.com/user-attachments/assets/fb19bbdb-8e32-45c4-9033-5eb5efc92a7d" alt="matriz correlação smote" style="width:600px; height:auto;">

Na reprodução, as relações entre variáveis são preservadas, com padrões consistentes com os do artigo original, reforçando a eficácia da técnica.

---

## Tabela de Comparação das Variáveis

| Variável                       | Categoria                                      | Artigo (%) | Reprodução (%) | Diferença (%) |
|--------------------------------|------------------------------------------------|------------|----------------|---------------|
| **Age recode with <1 year olds** | **10-14 years**                               | 0.0058     | 0.0056         | -0.0002       |
|                                | **15-19 years**                                | 0.0170     | 0.0168         | -0.0002       |
|                                | **20-24 years**                                | 0.1210     | 0.1216         | +0.0006       |
|                                | **25-29 years**                                | 0.3560     | 0.3554         | -0.0006       |
|                                | **30-34 years**                                | 0.7920     | 0.7912         | -0.0008       |
|                                | **35-39 years**                                | 1.4670     | 1.4664         | -0.0006       |
|                                | **40-44 years**                                | 2.9560     | 2.9553         | -0.0007       |
|                                | **45-49 years**                                | 5.2600     | 5.2597         | -0.0003       |
|                                | **50-54 years**                                | 9.6540     | 9.6534         | -0.0006       |
|                                | **55-59 years**                                | 10.1810    | 10.1809        | -0.0001       |
| **Sex**                        | **Male**                                       | 52.80      | 52.8010        | +0.0010       |
|                                | **Female**                                     | 47.20      | 47.1990        | -0.0010       |

---

## Observações

- **Diferenças Pequenas**: As variações de proporções entre o artigo original e a reprodução são mínimas, indicando boa correspondência entre os dados.
- **Consistência Geral**: Categorias como *Age recode*, *Sex* e *Race recode* mostram forte consistência.
- **Possíveis Variações**: Pequenas diferenças podem ser explicadas por ajustes no pré-processamento ou arredondamento.

---

## Conclusão

Os resultados mostram padrões gerais consistentes entre o artigo original e a reprodução, com pequenas variações em variáveis específicas. As técnicas de balanceamento (undersampling e SMOTE) demonstraram eficácia em ambos os cenários, reforçando a importância do detalhamento metodológico para garantir a reprodutibilidade em estudos científicos.
