# Comparação de Matrizes de Correlação: Artigo Original vs. Reprodução

Abaixo apresentamos as matrizes de correlação para os diferentes métodos de balanceamento (undersampling e SMOTE) utilizadas no artigo original e em nossa reprodução. As imagens em **tons roxos** referem-se aos gráficos apresentados no **artigo original**, enquanto as imagens em **tons azuis** são as matrizes geradas a partir da **reprodução** com base nas instruções fornecidas no artigo. Esta análise permite comparar o recorte realizado no estudo original com os resultados obtidos em nossa reprodução.

---

## Matriz de Correlação - Undersampling (Artigo Original)

<img src="https://github.com/user-attachments/assets/f5419f04-8c69-406e-9b73-83449e115f9f" alt="matriz correlação undersampling artigo" style="width:600px; height:auto;">

Esta matriz mostra a correlação entre as variáveis do dataset com a aplicação de undersampling, como representado no artigo original. Observa-se que algumas variáveis, como **Histologic Type ICD-O-3** e **ICD-O-3 Hist/behavior**, apresentam correlação extremamente alta, refletindo a dependência esperada entre essas características. Além disso, a variável alvo **Liver and/or Lung Metastasis** tem uma relação moderada com variáveis como **Tumor Deposits** e **Derived AJCC N**.

---

## Matriz de Correlação - Undersampling (Reprodução)

<img src="https://github.com/user-attachments/assets/d52029c3-6173-4f68-96c5-4705e07ace35" alt="matriz correlação undersampling" style="width:600px; height:auto;">

Nesta matriz, gerada pela reprodução com base nas instruções fornecidas no artigo, observa-se que os padrões de correlação são semelhantes aos do artigo original, especialmente em variáveis como **Histologic Type ICD-O-3** e **ICD-O-3 Hist/behavior**. No entanto, a correlação entre a variável alvo **Liver and/or Lung Metastasis** e **Tumor Deposits** é ligeiramente menor, possivelmente devido a variações nos dados ou no pré-processamento.

---

## Matriz de Correlação - SMOTE (Artigo Original)

<img src="https://github.com/user-attachments/assets/6910da25-f803-437b-b392-fab0884bc44b" alt="matriz correlação smote artigo" style="width:600px; height:auto;">

A matriz do artigo original com SMOTE apresenta correlações que preservam os padrões das variáveis originais, enquanto fortalece ligeiramente as relações com a variável alvo. Por exemplo, a correlação entre **Tumor Deposits** e **Liver and/or Lung Metastasis** é mais pronunciada, refletindo o impacto do oversampling na classe minoritária.

---

## Matriz de Correlação - SMOTE (Reprodução)

<img src="https://github.com/user-attachments/assets/fb19bbdb-8e32-45c4-9033-5eb5efc92a7d" alt="matriz correlação smote" style="width:600px; height:auto;">

Na reprodução com SMOTE, observa-se uma preservação consistente das relações entre variáveis. A correlação entre **Tumor Deposits** e a variável alvo é semelhante à apresentada no artigo original, reforçando a eficácia da técnica de oversampling em manter as características do dataset original. Isso demonstra como as instruções do artigo permitem replicar os padrões observados no estudo original.

---

## Conclusão

As matrizes de correlação reproduzidas mostram padrões gerais consistentes com os apresentados no artigo original. Embora pequenas diferenças sejam observadas em variáveis específicas, como **Tumor Deposits**, as estratégias de balanceamento (undersampling e SMOTE) demonstram ser eficazes tanto no artigo quanto na reprodução. Essa comparação destaca como o recorte realizado no artigo pode ser avaliado e replicado com sucesso através das instruções fornecidas no mesmo, evidenciando a importância do detalhamento metodológico para garantir reprodutibilidade em estudos científicos.
