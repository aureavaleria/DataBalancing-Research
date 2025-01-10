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
# Comparação de Variáveis Relacionadas à Metástase no Fígado: Artigo vs. Reprodução

Esta comparação avalia as distribuições de variáveis relacionadas à metástase no fígado, considerando dados do **artigo original** e da **reprodução**. Abaixo, apresentamos tabelas cruzadas organizadas para cada variável-chave.

# Comparação entre a Tabela 2 e as Tabelas de Contingência

## Comparação Geral

Os dados apresentados na **Tabela 2** e nas **Tabelas de Contingência** são consistentes em muitos aspectos, mas algumas diferenças específicas foram observadas. Abaixo, destacamos as principais comparações entre as categorias.

---

## Comparação de Idade

| Categoria de Idade | Com Metástase (Tabela 2) | Sem Metástase (Tabela 2) | Contingência Binary Mets: 1 (%) | Contingência Binary Mets: 0 (%) |
|--------------------|--------------------------|--------------------------|---------------------------------|---------------------------------|
| <60               | 27.2%                   | 31.2%                   | 26.9%                          | 31.3%                          |
| ≥60               | 72.8%                   | 68.8%                   | 73.1%                          | 68.7%                          |

**Observação:** A distribuição de idade entre as duas tabelas é praticamente consistente, com diferenças mínimas atribuídas ao arredondamento ou ao recorte dos dados.

---

## Comparação de Sexo

| Sexo      | Com Metástase (Tabela 2) | Sem Metástase (Tabela 2) | Contingência Binary Mets: 1 (%) | Contingência Binary Mets: 0 (%) |
|-----------|--------------------------|--------------------------|---------------------------------|---------------------------------|
| Feminino | 47.4%                   | 47.3%                   | 43.4%                          | 47.9%                          |
| Masculino | 52.6%                   | 52.7%                   | 56.6%                          | 52.1%                          |

**Observação:** Pequenas diferenças foram encontradas na distribuição por sexo. No entanto, o padrão geral permanece alinhado.

---

## Comparação de Raça

| Raça       | Com Metástase (Tabela 2) | Sem Metástase (Tabela 2) | Contingência Binary Mets: 1 (%) | Contingência Binary Mets: 0 (%) |
|------------|--------------------------|--------------------------|---------------------------------|---------------------------------|
| Branca    | 77.9%                   | 77.8%                   | 78.3%                          | 78.2%                          |
| Negra     | 9.4%                    | 8.9%                    | 9.6%                           | 9.2%                           |
| Outras    | 12.7%                   | 13.3%                   | 12.1%                          | 12.6%                          |

**Observação:** A proporção de raça é altamente consistente entre as tabelas, com desvios mínimos.

---

## Comparação de Estágio T (Derived AJCC T)

| Estágio T | Com Metástase (Tabela 2) | Sem Metástase (Tabela 2) | Contingência Binary Mets: 1 (%) | Contingência Binary Mets: 0 (%) |
|-----------|--------------------------|--------------------------|---------------------------------|---------------------------------|
| T1        | 12.2%                   | 20.6%                   | 11.1%                          | 19.9%                          |
| T2        | 8.0%                    | 13.3%                   | 7.3%                           | 13.5%                          |
| T3        | 42.9%                   | 45.8%                   | 44.3%                          | 44.8%                          |
| T4        | 24.0%                   | 14.4%                   | 26.5%                          | 12.9%                          |
| TX        | 12.9%                   | 5.9%                    | 10.8%                          | 8.9%                           |

**Observação:** As distribuições dos estágios T são semelhantes, com algumas variações na proporção de TX entre as tabelas.

---

## Comparação de Grau

| Grau        | Com Metástase (Tabela 2) | Sem Metástase (Tabela 2) | Contingência Binary Mets: 1 (%) | Contingência Binary Mets: 0 (%) |
|-------------|--------------------------|--------------------------|---------------------------------|---------------------------------|
| Grau I     | 5.9%                    | 7.7%                    | 4.8%                           | 7.6%                           |
| Grau II    | 58.7%                   | 66.8%                   | 59.4%                          | 65.4%                          |
| Grau III   | 18.3%                   | 13.5%                   | 18.5%                          | 14.2%                          |
| Grau IV    | 3.6%                    | 2.6%                    | 3.9%                           | 2.4%                           |
| Desconhecido | 13.5%                  | 9.4%                    | 13.4%                          | 10.3%                          |

**Observação:** As proporções de Grau II e Grau III são próximas entre as tabelas, mas diferenças foram notadas nas categorias desconhecidas.

---

## Conclusão
- Os resultados mostram padrões gerais consistentes entre o artigo original e a reprodução, com pequenas variações em variáveis específicas. As técnicas de balanceamento (undersampling e SMOTE) demonstraram eficácia em ambos os cenários, reforçando a importância do detalhamento metodológico para garantir a reprodutibilidade em estudos científicos.
- **Consistência Geral:** As tabelas apresentaram padrões similares, com variações mínimas atribuídas ao particionamento e ao arredondamento dos dados.
- **Destaques:** As variáveis *Idade*, *Sexo*, *Raça* e *Estágio T* são consistentes entre os dois conjuntos de tabelas. Pequenas variações foram observadas em categorias mais específicas, como *Grau* e *TX*.
- **Variações:** Diferenças observadas podem ser atribuídas a diferenças na amostragem ou na metodologia de pré-processamento entre o estudo original e as análises realizadas.



