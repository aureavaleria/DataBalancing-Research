# Visão Geral — imbalanced-learn

A biblioteca [`imbalanced-learn`](https://imbalanced-learn.org/stable/) é a principal ferramenta em Python para tratar problemas de desbalanceamento de classes em aprendizado de máquina.  
Ela oferece uma ampla variedade de técnicas de oversampling (aumentar classe minoritária), undersampling (reduzir classe majoritária) e métodos combinados, todos integrados ao scikit-learn.

---

## Instalação

Você pode instalar a biblioteca via **pip**:
```bash
pip install imbalanced-learn
``` 

Também pode ser instalada com conda:

```bash
conda install -c conda-forge imbalanced-learn
``` 

## Principais Funcionalidades

- **Oversampling:**  
  - SMOTE  
  - BorderlineSMOTE  
  - KMeansSMOTE  
  - ADASYN  
  - SVMSMOTE  
  - SMOTENC (para dados categóricos)

- **Undersampling:**  
  - RandomUnderSampler  
  - TomekLinks  
  - NearMiss  
  - ClusterCentroids  
  - Outros

- **Métodos combinados:**  
  - SMOTEENN  
  - SMOTETomek

- **Integração com pipelines do scikit-learn:**  
  Suporta validação cruzada, grid search, e outras funcionalidades do scikit-learn.
