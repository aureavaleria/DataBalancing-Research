## **Principais Pontos do Artigo**

Este artigo realiza uma **revisão sistemática** sobre modificações no método SMOTE (Synthetic Minority Oversampling Technique), com o objetivo de resolver problemas relacionados ao **desbalanceamento de dados** em aprendizado de máquina. Os principais pontos incluem:

1. **Problemas do SMOTE original**:
   - Introduz **ruído** ao gerar dados sintéticos.
   - Pode gerar **sobreamostragem** nas fronteiras de decisão.
   - Ignora desbalanceamento dentro de clusters.

2. **Métodos Modificados**:
   Diversas variações do SMOTE foram propostas para resolver essas limitações:
   - **SMOTE-LOF**: Combina SMOTE com o Local Outlier Factor para identificar e remover ruídos.
   - **ASN-SMOTE**: Seleciona sintetizadores adaptativos para melhorar a qualidade dos dados gerados.
   - **LR-SMOTE**: Utiliza o conceito de raio seguro para limitar a criação de amostras sintéticas.
   - **Clustering-SMOTE**: Integra métodos de clusterização (como K-means) com SMOTE para gerar dados sintéticos mais equilibrados.
   - **Outlier-SMOTE**: Prioriza amostragem de outliers distantes para lidar com casos extremos.
   - **KNNOR**: Aplica filtragem com kNN para eliminar ruídos e selecionar amostras seguras.

3. **Métricas de Avaliação**:
   Os métodos são avaliados utilizando métricas como **acurácia, F1-measure, recall, AUC** e **G-mean**.

4. **Fraquezas Persistentes**:
   Apesar das melhorias, alguns métodos ainda apresentam desafios, como a **determinação do número ideal de clusters** e a **eliminação inadequada de ruídos**.

A tabela a seguir resume os métodos modificados e suas características.

---

## **Tabela Resumida dos Métodos Modificados**

| **Referências**        | **Método**                                           | **Conjunto de Dados**                                                                                              | **Métricas de Avaliação**                              | **Fraquezas**                                                                                          |
|-------------------------|------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Asniar et al. (2022)    | SMOTE-LOF                                            | Pima, Haberman, Glass                                                                                            | Acurácia, precisão, recall, F1-measure, AUC          | Ignora informações nos dados outliers                                                                  |
| Yi et al. (2022)        | ASN-SMOTE                                            | Pima, Haberman, Ecoli, New Thyroid, Car, Iris, Seeds, Wine, Dermatology, Pageblock, Glass 0–6, Yeast 0–8          | G-mean, F1-measure                                  | O ruído nos dados não é removido                                                                       |
| Liang et al. (2020)     | LR-SMOTE                                             | Pima, Haberman, Blood, Abalon                                                                                    | F1-measure, recall, G-mean                           | 1. Determinação do número ótimo de clusters<br>2. Ignora a proporção da classe minoritária em cada cluster |
| Duan et al. (2022)      | MeanRadius-SMOTE                                     | PHM                                                                                                              | Acurácia, F1-measure                                 | Dados ruidosos são envolvidos                                                                          |
| Douzas e Bacao (2019)   | Geometric-SMOTE                                      | Pima, Haberman, Breast, Heart, Liver, Wine, Iris, Glass, Yeast, Vehicle, New Thyroid, Ecoli, Eucalyptus, Page Block | Acurácia, AUC, F1-measure, G-mean                    | G-SMOTE pode produzir amostras artificiais excessivas da classe minoritária                             |
| Revathi e Ramyachitra (2021) | Borderline SMOTE           | Ecoli, Yeast, Abalon, Glass, Vowel, Page, Block, Statlog                                                        | Acurácia                                             | Foco nas áreas de decisão leva ao oversampling                                                         |
| Jadwal et al. (2022)    | Clustering Espectral e SMOTE                         | P2P Lending                                                                                                     | Acurácia, F1-measure, G-mean                         | 1. Ruído nos dados não é tratado<br>2. Não determina o número ideal de clusters                         |
| Yi et al. (2021)        | SMOTE com Clustering de Minorias                     | Pima, Breast, Glass, Iris, Wine, Phoneme, Segment, Yeast, Vowel, Abalon, Ecoli                                   | Acurácia, F1-measure, G-mean, recall, precisão       | 1. Ruído nos dados não é tratado<br>2. Não determina o número ideal de clusters                         |
| Fonseca et al. (2021)   | SMOTE com K-means                                    | Botswana, Pavia, Kennedy, Salinas                                                                               | Acurácia, F1-measure, G-mean                         | 1. Ruído nos dados não é tratado<br>2. Não determina o número ideal de clusters                         |
| Feng et al. (2020)      | CUSS (SMOTE com Undersampling Clusterizado)          | Pima, Haberman, Glass, Ecoli, Vehicle, Yeast                                                                    | AUC                                                 | 1. Ruído nos dados não é tratado<br>2. Ignora a proporção de classes                                    |
| Liu et al. (2023)       | KM-SMOTE                                             | Rockburst data                                                                                                  | Acurácia                                             | Ruído nos dados não é tratado                                                                          |
| Dai et al. (2023)       | Modificação de Métricas de Distância do SMOTE        | Pima, Haberman, Ecoli, New Thyroid, Wisconsin, Vehicle                                                          | Acurácia, F1-measure, kappa, recall specificity       | -                                                                                                     |
| Turlapati e Prusty (2020)| Outlier-SMOTE                                       | Ecoli, Abalon, Yeast, Wine, Mammography                                                                         | Recall, precisão, F1-measure                         | Ruído próximo à classe majoritária não é tratado                                                       |
| Islam et al. (2022)     | KNNOR                                                | Pima, Haberman, New Thyroid, Glass, Ecoli                                                                       | F1-measure, G-mean                                   | Muitos parâmetros são necessários para balancear os dados                                              |
| Wei et al. (2022)       | SMOTE Aleatório Melhorado (IR-SMOTE)                 | Haberman, Breast, Ecoli, Yeast, Abalone, Pageblock, German                                                      | Acurácia, recall, especificidade, F1-measure, G-mean | 1. Ruído nos dados não é tratado<br>2. Ignora a proporção entre classes                                 |
| Gameng et al. (2019)    | Adasyn com Distância Manhattan                       | Dados de Graduados                                                                                              | Acurácia, recall, precisão, F1-measure               | Ruído nos dados não é tratado                                                                          |
| Liu (2022)              | SMOTE com Importância                                | Pima, Haberman, Glass, Ecoli, Yeast, Vehicle                                                                    | F1-measure, G-mean                                   | Ruído nos dados não é tratado                                                                          |
| Ghorab et al. (2023)    | SMOTE Mean-Shift                                     | Pima, Haberman, Blood                                                                                           | AUC, acurácia                                        | 1. Dados outliers são removidos<br>2. Ignora a proporção de classes                                     |

O artigo apresenta **modificações no SMOTE** como soluções para o desbalanceamento de dados, destacando abordagens híbridas e específicas que mitigam limitações do método original. Apesar das melhorias, desafios como **tratamento de ruído** e **otimização de clusters** ainda demandam investigações adicionais.

            
## **Referências**

Yi, X., Xu, Y., Hu, Q., Krishnamoorthy, S., Li, W., & Tang, Z. (2022). ASN-SMOTE: A synthetic minority oversampling method with adaptive qualified synthesizer selection. *Complex & Intelligent Systems*, 8(3), 2247–2272. https://doi.org/10.1007/s40747-021-00638-w

Asniar, A., Maulidevi, N. U., & Surendro, K. (2022). SMOTE-LOF for noise identification in imbalanced data classification. *Journal of King Saud University - Computer Science*, 34(6), 3413–3423. https://doi.org/10.1016/j.jksuci.2021.01.014

Liang, X. W., Jiang, A. P., Li, T., Xue, Y. Y., & Wang, G. T. (2020). LR-SMOTE: An improved unbalanced data set oversampling based on K-means and SVM. *Knowledge-Based Systems*, 196(May), 1–10. https://doi.org/10.1016/j.knosys.2020.105845

Duan, F., Zhang, S., Yan, Y., & Cai, Z. (2022). An oversampling method of unbalanced data for mechanical fault diagnosis based on MeanRadius-SMOTE. *Sensors*, 22(14), 1–15. https://doi.org/10.3390/s22145166

Douzas, G., & Bacao, F. (2019). Geometric SMOTE: A geometrically enhanced drop-in replacement for SMOTE. *Information Sciences*, 501, 118–135. https://doi.org/10.1016/j.ins.2019.06.007

Revathi, M., & Ramyachitra, D. (2021). A modified Borderline-SMOTE with noise reduction in imbalanced datasets. *Wireless Personal Communications*, 121(3), 1659–1680. https://doi.org/10.1007/s11277-021-08690-y

Jadwal, P. K., Jain, S., Pathak, S., & Agarwal, B. (2022). Improved resampling algorithm through a modified oversampling approach based on spectral clustering and SMOTE. *Microsystem Technologies*, 28(12), 2669–2677. https://doi.org/10.1007/s00542-022-05287-8

Yi, H., Jiang, Q., Yan, X., & Wang, B. (2021). Imbalanced classification based on minority clustering synthetic minority oversampling technique with wind turbine fault detection application. *IEEE Transactions on Industrial Informatics*, 17(9), 5867–5875. https://doi.org/10.1109/TII.2020.3046566

Fonseca, J., Douzas, G., & Bacao, F. (2021). Improving imbalanced land cover classification with K-means SMOTE: Detecting and oversampling distinctive minority spectral signatures. *Information*, 12(7), 1–20. https://doi.org/10.3390/info12070266

Feng, S., Zhao, C., & Fu, P. (2020). A cluster-based hybrid sampling approach for imbalanced data classification. *Review of Scientific Instruments*.

Liu, Q., et al. (2023). Application of KM-SMOTE for rockburst intelligent prediction. *Tunnelling and Underground Space Technology*, 138(October), 1–10. https://doi.org/10.1016/j.tust.2023.105180

Dai, Q., Liu, J. W., & Zhao, J. L. (2023). Distance-based arranging oversampling technique for imbalanced data. *Neural Computing and Applications*, 35(2), 1323–1342. https://doi.org/10.1007/s00521-022-07828-8

Turlapati, V. P. K., & Prusty, M. R. (2020). Outlier-SMOTE: A refined oversampling technique for improved detection of COVID-19. *Intelligence-Based Medicine*, 3–4(November), 1–10. https://doi.org/10.1016/j.ibmed.2020.100023

Islam, A., Belhaouari, S. B., Rehman, A. U., & Bensmail, H. (2022). KNNOR: An oversampling technique for imbalanced datasets. *Applied Soft Computing*, 115, 1–18. https://doi.org/10.1016/j.asoc.2021.108288

Wei, G., Mu, W., Song, Y., & Dou, J. (2022). An improved and random synthetic minority oversampling technique for imbalanced data. *Knowledge-Based Systems*, 248(July), 1–13. https://doi.org/10.1016/j.knosys.2022.108839

Gameng, H. A., Gerardo, B. D., & Medina, R. P. (2019). A modified adaptive synthetic SMOTE approach in graduation success rate classification. *International Journal of Advanced Trends in Computer Science and Engineering (IJATCSE)*, 8(6), 3053–3057. https://doi.org/10.30534/ijatcse/2019/63862019

Liu, J. (2022). Importance-SMOTE: A synthetic minority oversampling method for noisy imbalanced data. *Soft Computing*, 26(2), 1141–1163.

Ghorab, A. S., Ashour, W. M., & Abudalfa, S. I. (2023). An adaptive oversampling method for imbalanced datasets based on Mean-Shift and SMOTE. In *CBT 2022: Explore Business, Technology Opportunities and Challenges After the Covid-19 Pandemic* (pp. 13–23). https://doi.org/10.1007/978-3-031-08954-1_2
