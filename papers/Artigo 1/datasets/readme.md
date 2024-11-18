# README - Análise e Exploração de Dados com Base SEER

Este repositório contém notebooks e arquivos relacionados à análise exploratória e estatística de dados clínicos e demográficos provenientes da base SEER. O objetivo principal é identificar padrões relevantes e realizar análises preditivas no contexto de metástases hepáticas e pulmonares em pacientes com câncer colorretal.

## Conteúdo do Repositório

### **`Análise_Exploratória_de_Dados.ipynb`**  
Notebook dedicado à análise exploratória inicial da base de dados, incluindo gráficos descritivos para variáveis categóricas e contínuas. 

### **`Análise_Estatística.ipynb`**  
Notebook focado em análises estatísticas avançadas, como testes de associação (Qui-Quadrado e Fisher), correlação entre variáveis e regressão logística para prever fatores relacionados à metástase.

### **`Base_de_dados_sintetica.ipynb`**  
Notebook que apresenta o processo de criação e manipulação de uma base de dados sintética para experimentação e validação de técnicas, baseada na estrutura original.

### **Arquivos de Dados:**
- **`export.csv`**: Base de dados original extraída da SEER, contendo variáveis clínicas e demográficas relevantes.
  # Descrição da Base de Dados

O repositório **DataBalancing-Research** utiliza diferentes bases de dados para explorar e implementar técnicas de balanceamento de dados, com foco principal em contextos médicos. Entre as bases de dados utilizadas, destacamos o **SEER** (Surveillance, Epidemiology, and End Results Program), amplamente reconhecido por fornecer informações detalhadas sobre o diagnóstico, tratamento e prognóstico de pacientes com câncer.

Abaixo, apresentamos duas tabelas que descrevem as variáveis selecionadas e os filtros aplicados na base de dados SEER, bem como os significados detalhados de cada atributo, para auxiliar na compreensão e replicação dos experimentos.

---

## Tabela 1: Correspondência de Variáveis e Filtros Aplicados no Dataset SEER

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

## Tabela 2: Descrição Detalhada das Variáveis Utilizadas no Estudo

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

### **`readme`**  
Arquivo de documentação inicial sobre os objetivos e conteúdos do repositório.
