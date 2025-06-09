versão 5 (testes): Código base para fazer os testes

Teste 01: MST-SMOTE Clustering é uma técnica de balanceamento que combina agrupamento (como KMeans, DBSCAN ou AHC) com a geração de amostras sintéticas ao longo das arestas da árvore geradora mínima (MST) dentro de cada cluster da classe minoritária. Isso permite gerar exemplos sintéticos de forma estruturada, respeitando a geometria local dos dados e evitando regiões ruidosas ou dispersas.

Teste 02: ClinSMOTE-SEER é uma variação do SMOTE que leva em conta informações clínicas ao gerar exemplos sintéticos. Ele realiza o balanceamento dentro de grupos estratificados por variáveis clínicas relevantes (como estágio T/N, grau tumoral e níveis de CEA), garantindo que as amostras geradas sejam clinicamente coerentes. Além disso, evita gerar exemplos em regiões de baixa densidade ou com alto ruído, aumentando a qualidade e a interpretabilidade dos dados sintéticos.
