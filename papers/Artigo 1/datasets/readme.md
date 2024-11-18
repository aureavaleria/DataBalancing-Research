# README - Análise e Exploração de Dados com Base SEER

Este repositório contém notebooks e arquivos relacionados à análise exploratória e estatística de dados clínicos e demográficos provenientes da base SEER. O objetivo principal é identificar padrões relevantes e realizar análises preditivas no contexto de metástases hepáticas e pulmonares em pacientes com câncer colorretal.

## Conteúdo do Repositório

### **`Análise_Exploratória_de_Dados.ipynb`**  
Notebook dedicado à análise exploratória inicial da base de dados, incluindo gráficos descritivos para variáveis categóricas e contínuas. 

### **`Análise_Estatística.ipynb`**  
Notebook focado em análises estatísticas avançadas, como testes de associação (Qui-Quadrado e Fisher), correlação entre variáveis e regressão logística para prever fatores relacionados à metástase.

### **`Base_de_dados_sintetica.ipynb`**  
Notebook que apresenta o processo de criação e manipulação de uma base de dados sintética para experimentação e validação de técnicas, baseada na estrutura original.

# **Arquivos de Dados:**
- ## **`export.csv`**: 
  ## Descrição da Base de Dados

A base de dados utilizada neste repositório foi gerada com base no artigo científico **"Machine learning for predicting liver and/or lung metastasis in colorectal cancer: A retrospective study based on the SEER database"**, que fornece uma estrutura metodológica robusta para a seleção e filtragem de variáveis relevantes. Esse artigo serviu como referência para definir as variáveis incluídas, os filtros aplicados e os critérios de exclusão utilizados no processamento dos dados.

Abaixo, apresentamos duas tabelas que descrevem as variáveis selecionadas e os filtros aplicados na base SEER, bem como os significados detalhados de cada atributo. Estas tabelas foram organizadas para auxiliar na compreensão e replicação dos experimentos e garantir a rastreabilidade dos processos utilizados.

---

### Tabela 1: Correspondência de Variáveis e Filtros Aplicados no Dataset SEER

Esta tabela lista as variáveis usadas nos experimentos e sua correspondência no dataset SEER, além de filtros aplicados para garantir a consistência e relevância dos dados analisados.

| **Nome no Artigo**      | **Nome no Dataset SEER**                           | **Filtro Citado no Artigo**                                                                            |
|--------------------------|----------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| Age                     | Age recode with <1 year olds                       |                                                                                                        |
| Sex                     | Sex                                                |                                                                                                        |
| Race                    | Race recode (White, Black, Other)                  |                                                                                                        |
| Hispanic                | Origin recode NHIA (Hispanic, Non-Hisp)            |                                                                                                        |
| Marital status          | Marital status at diagnosis                        |                                                                                                        |
| Histological type       | Histologic Type ICD-O-3                            | 8140/3, 8210/3, 8261/3, 8263/3, 8480/3, 8490/3 <br> Excluir casos com tipo histológico desconhecido.  |
| Grade                   | Grade Recode (thru 2017)                           |                                                                                                        |
| Primary Site            | Primary Site                                       | C18.0, C18.1, C18.2, C18.3, C18.4, C18.5, etc.                                                        |
| T stage                 | Derived AJCC T, 7th ed (2010-2015)                 | Excluir casos com estágio T desconhecido.                                                             |
| N stage                 | Derived AJCC N, 7th ed (2010-2015)                 | Excluir casos com estágio N desconhecido.                                                             |
| Tumor size              | CS tumor size (2004-2015)                          | Excluir casos com tamanho do tumor desconhecido.                                                      |
| CEA                     | CEA Pretreatment Interpretation Recode (2010+)     |                                                                                                        |
| Tumor deposits          | Tumor Deposits Recode (2010+)                      |                                                                                                        |
| Liver and/or lung Metastasis | SEER Combined Mets at DX-lung (2010+), <br> SEER Combined Mets at DX-liver (2010+) | Excluir casos com metástase pulmonar ou hepática desconhecida.                                        |
| Survival months         | Survival months                                    | Excluir casos com informações de sobrevivência desconhecidas.                                         |
| Treatment methods       | -                                                  | Excluir casos com métodos de tratamento desconhecidos.                                                |
| Bone Metastasis         | SEER Combined Mets at DX-bone (2010+)              | Excluir casos com status de metástase óssea desconhecido.                                             |
| Year                    | -                                                  | Pacientes diagnosticados com câncer colorretal entre 2010 e 2015.                                     |

---

### Tabela 2: Descrição Detalhada das Variáveis Utilizadas no Estudo

Esta tabela apresenta uma descrição mais aprofundada das variáveis analisadas, incluindo seus significados e fontes, para contextualizar o uso dessas informações nos experimentos e modelagens realizados.

| **Variável**            | **Descrição Detalhada**                                                                                                                                                 | **Referências**                     |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------|
| Histological Types      | Classificações de câncer baseadas nas características microscópicas das células tumorais, conforme descrito no manual ICD-O-3.                                         | WHO, 2000                           |
| Marital Status          | Estado civil dos pacientes, coletado para analisar fatores como suporte social, adesão ao tratamento e prognóstico.                                                   | NCI SEER, 2021                      |
| Grade                  | Avaliação da agressividade das células tumorais com base na velocidade de crescimento e grau de diferenciação.                                                         | EDGE et al., 2010                   |
| Primary Tumor Site      | Localização inicial do tumor no corpo. No caso de câncer colorretal, o SEER utiliza códigos específicos (C18.0 a C20.9) para diferentes partes do cólon e reto.        | WHO, 2000                           |
| T Stage                | Parte do sistema de estadiamento TNM da AJCC 7ª edição, descrevendo o tamanho e extensão do tumor primário.                                                             | EDGE et al., 2010                   |
| N Stage                | Parte do sistema TNM que descreve a extensão de disseminação para linfonodos próximos.                                                                                  | EDGE et al., 2010                   |
| Tumor Size              | Medida física do tumor, registrada no SEER em milímetros ou centímetros.                                                                                               | NCI SEER, 2021                      |
| CEA                     | Marcador tumoral que pode estar elevado no sangue de pacientes com certos tipos de câncer.                                                                             | DUFFY et al., 2007                  |
| Tumor Deposits          | Pequenos depósitos de células tumorais no tecido ao redor do tumor primário, podendo influenciar o prognóstico.                                                        | EDGE et al., 2010                   |
| Site Codes              | Códigos anatômicos no ICD-O-3 (C18.0 a C20.9) que indicam onde o tumor está localizado.                                                                                | WHO, 2000                           |


 
- **`bdsintetico.csv`**: Base de dados sintética gerada para testes de técnicas experimentais.
A base de dados sintética utilizada neste repositório foi desenvolvida a partir dos percentuais descritos na tabela retirada **integralmente** do artigo **"Machine learning for predicting liver and/or lung metastasis in colorectal cancer: A retrospective study based on the SEER database"**. Esta tabela apresenta as características clínicas e patológicas dos pacientes da base SEER e foi essencial para guiar a construção da base sintética, permitindo a reprodução fiel das distribuições originais dos dados.

A base sintética foi criada replicando as distribuições percentuais das variáveis presentes na tabela, como idade, gênero, raça, estágio do tumor (T/N), tamanho do tumor, e outros atributos clínicos relevantes. O objetivo é garantir que a base de dados seja suficientemente representativa para validar os experimentos descritos no artigo, sem a necessidade de acesso direto à base de dados descrita no artigo, respeitando restrições de uso e privacidade.

O propósito desta base é servir como um recurso para a reprodução do passo a passo descrito no artigo, permitindo a replicação de experimentos e a avaliação das técnicas de aprendizado de máquina aplicadas à predição de metástases hepáticas e/ou pulmonares em pacientes com câncer colorretal. Dessa forma, a base sintética oferece uma alternativa prática e confiável para o desenvolvimento e validação de modelos experimentais.

A tabela abaixo, extraída diretamente do artigo, detalha as distribuições percentuais e as características utilizadas na construção da base de dados sintética.

- ### Tabela 1: Características Clínicas e Patológicas da Base de Dados SEER e do Conjunto de Validação Externa

| **Categoria**          | **Validação Externa (N = 196)** | **Base de Dados SEER (N = 51265)** | **P-Valor** |
|-------------------------|---------------------------------|------------------------------------|-------------|
| **Idade (anos)**        |                                 |                                    | 0.164       |
| <60                    | 51 (26.0%)                     | 15692 (30.6%)                     |             |
| ≥60                    | 145 (74.0%)                    | 35573 (69.4%)                     |             |
| **Gênero**              |                                 |                                    | 0.500       |
| Feminino               | 88 (44.9%)                     | 24253 (47.3%)                     |             |
| Masculino              | 108 (55.1%)                    | 27012 (52.7%)                     |             |
| **Raça**                |                                 |                                    | <0.001      |
| Branco                 | 196 (100.0%)                   | 39011 (77.6%)                     |             |
| Negro                  | 0 (0.0%)                       | 4601 (9.0%)                       |             |
| Outro                  | 0 (0.0%)                       | 6763 (13.2%)                      |             |
| **Hispânico**           |                                 |                                    | <0.001      |
| Não                   | 0 (0.0%)                       | 47081 (91.8%)                     |             |
| Sim                   | 196 (100.0%)                   | 4184 (8.2%)                       |             |
| **Estado Civil**        |                                 |                                    | <0.001      |
| Casado                | 196 (100.0%)                   | 21448 (41.9%)                     |             |
| Solteiro              | 0 (0.0%)                       | 27257 (53.9%)                     |             |
| Desconhecido          | 0 (0.0%)                       | 2560 (5.1%)                       |             |
| **Tipo Histológico**    |                                 |                                    | <0.001      |
| Adenocarcinoma        | 163 (83.2%)                    | 47077 (91.9%)                     |             |
| Adenocarcinoma mucinoso | 28 (14.3%)                    | 3570 (7.0%)                       |             |
| Células em anel de sinete | 5 (2.5%)                    | 618 (1.2%)                        |             |
| **Grau**                |                                 |                                    | <0.001      |
| Grau I                | 26 (13.3%)                     | 3818 (7.5%)                       |             |
| Grau II               | 142 (72.5%)                    | 33642 (65.6%)                     |             |
| Grau III              | 24 (12.2%)                     | 7297 (14.2%)                      |             |
| Grau IV               | 1 (0.5%)                       | 424 (0.8%)                        |             |
| Desconhecido          | 3 (1.5%)                       | 5084 (9.9%)                       |             |
| **Localização do Tumor** |                                 |                                    | 0.424       |
| Ceco                  | 24 (12.2%)                     | 8338 (16.3%)                      |             |
| Apêndice              | 9 (5.0%)                       | 833 (1.6%)                        |             |
| Cólon ascendente      | 17 (8.7%)                      | 10765 (21.0%)                     |             |
| Flexura hepática do cólon | 4 (2.0%)                   | 2464 (4.8%)                       |             |
| Cólon transverso      | 8 (4.1%)                       | 4291 (8.4%)                       |             |
| Flexura esplênica do cólon | 4 (2.0%)                  | 1734 (3.4%)                       |             |
| Cólon descendente     | 22 (11.2%)                     | 7337 (14.3%)                      |             |
| Sigmoide              | 84 (42.9%)                     | 10225 (20.0%)                     |             |
| Lesão sobreposta do cólon | 0 (0.0%)                   | 108 (0.2%)                        |             |
| Cólon, não especificado | 9 (4.6%)                     | 695 (1.4%)                        |             |
| **Junção Retossigmoide** | 3 (1.5%)                     | 3879 (7.6%)                       |             |
| **Reto, não especificado** | 48 (24.5%)               | 10526 (20.5%)                     |             |
| **Estágio T (T stage)** |                                 |                                    | <0.001      |
| T1                    | 6 (3.1%)                       | 6246 (12.5%)                      |             |
| T2                    | 17 (8.7%)                      | 9612 (19.9%)                      |             |
| T3                    | 129 (65.8%)                    | 24694 (51.6%)                     |             |
| T4                    | 44 (22.4%)                     | 8151 (15.9%)                      |             |
| Desconhecido (TX)     | 0 (0.0%)                       | 3561 (7.0%)                       |             |
| **Estágio N (N stage)** |                                 |                                    | 0.849       |
| N0                    | 112 (57.1%)                    | 29691 (57.9%)                     |             |
| N1                    | 56 (28.6%)                     | 15193 (29.7%)                     |             |
| N2                    | 28 (14.3%)                     | 6733 (13.4%)                      |             |
| Desconhecido (NX)     | 0 (0.0%)                       | 1710 (3.4%)                       |             |
| **Tamanho do Tumor**   |                                 |                                    | 0.018       |
| < 5 cm                | 99 (50.5%)                     | 25436 (49.6%)                     |             |
| ≥ 5 cm                | 97 (49.5%)                     | 17524 (34.2%)                     |             |
| Desconhecido          | 0 (0.0%)                       | 8305 (16.2%)                      |             |
| **CEA**                |                                 |                                    | <0.001      |
| Negativo              | 105 (53.6%)                    | 15928 (31.0%)                     |             |
| Limítrofe             | 58 (29.6%)                     | 17136 (33.4%)                     |             |
| Positivo              | 28 (14.3%)                     | 8621 (16.8%)                      |             |
| Desconhecido          | 5 (2.6%)                       | 20680 (40.7%)                     |             |
| **Depósitos Tumorais** |                                 |                                    | <0.001      |
| Não                   | 178 (90.8%)                    | 47982 (93.6%)                     |             |
| Sim                   | 18 (9.2%)                      | 2839 (5.6%)                       |             |
| Desconhecido          | 0 (0.0%)                       | 12722 (24.8%)                     |             |
| **Metástase Hepática/Pulmonar** |                       |                                    | 0.001       |
| Não                   | 180 (91.8%)                    | 42303 (82.5%)                     |             |
| Sim                   | 16 (8.2%)                      | 8962 (17.5%)                      |             |


### **`readme`**  
Arquivo de documentação inicial sobre os objetivos e conteúdos do repositório.
