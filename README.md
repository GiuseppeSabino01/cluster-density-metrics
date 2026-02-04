# The DBCV index outperforms AUCC, DISCO, CVDD, LCCV, and density-based variants of Davies-Bouldin, Dunn, and Calinski-Harabasz indices for unsupervised concave clustering internal evaluation

## Title
The DBCV index outperforms AUCC, DISCO, CVDD, LCCV, and density-based variants of Davies-Bouldin, Dunn, and Calinski-Harabasz indices for unsupervised concave clustering internal evaluation

---

## Description
This repository contains the code and scripts used to reproduce the experiments described in the paper:

**“The DBCV index outperforms AUCC, DISCO, CVDD, LCCV, and density-based variants of Davies–Bouldin, Dunn, and Calinski–Harabasz indices for unsupervised concave clustering internal evaluation.”**

The project focuses on the evaluation of internal clustering validation metrics for density-based clustering algorithms, especially in the presence of concave, nested, noisy, or arbitrarily shaped clusters.  
The repository includes implementations and comparisons of the following metrics:

- DBCV (Density-Based Clustering Validation)
- AUCC (Area Under the Clustering Curve)
- DISCO
- CVDD
- LCCV
- Density-Based Davies–Bouldin Index (DBDBI)
- Density-Based Calinski–Harabasz Index (DBCHI)
- Density-Based Dunn Index (DBDI)

Experiments are conducted on both synthetic datasets and real-world medical datasets.

---

## Dataset Information

### Synthetic Datasets
The synthetic datasets are generated programmatically and include the following shapes:

- Half Moons
- Shifting Circles
- Sparse Circles
- Tulip-shaped clusters
- Multishapes dataset

For each dataset, increasing levels of noise are added to progressively degrade the cluster structure.  
No external data files are required for synthetic datasets, as they are generated at runtime.

### Real-World Medical Datasets
The real datasets are derived from electronic health records and include:

- **Neuroblastoma**  
  Data derived from the cohort described in:  
  Ma Y., Zheng J., Feng J., Chen L., Dong K., Xiao X.  
  *Neuroblastomas in eastern China: a retrospective series study of 275 cases in a regional center.*  
  **PeerJ**, 6:e5665, 2018.  
  DOI: https://doi.org/10.7717/peerj.5665

- **Type 1 Diabetes**  
  Data informed by the following studies:  
  Takashi Y., Ishizu M., Mori H., Miyashita K., Sakamoto F., Katakami N., et al.  
  *Circulating osteocalcin as a bone-derived hormone is inversely correlated with body fat in patients with type 1 diabetes.*  
  **PLOS One**, 14(5):e0216416, 2019.  
  DOI: https://doi.org/10.1371/journal.pone.0216416  

- **Sepsis & Systemic Inflammatory Response Syndrome (SIRS)**  
  Data derived from the following sources:  
  Gucyetmez B., Atalan H.K.  
  *C-reactive protein and hemogram parameters for the non-sepsis systemic inflammatory response syndrome and sepsis: what do they mean?*  
  **PLOS One**, 11(2):e0148699, 2016.  
  DOI: https://doi.org/10.1371/journal.pone.0148699  

- **Heart Failure & Depression**  
  Data based on the cohort described in:  
  Jani B.D., Mair F.S., Roger V.L., Weston S.A., Jiang R., Chamberlain A.M.  
  *Comorbid depression and heart failure: a community cohort study.*  
  **PLOS One**, 11(6):e0158570, 2016.  
  DOI: https://doi.org/10.1371/journal.pone.0158570

- **Cardiac Arrest**  
  Data derived from:  
  Requena-Morales R., Palazón-Bru A., Rizo-Baeza M.M., Adsuar-Quesada J.M., Gil-Guillén V.F., Cortés-Castell E.  
  *Mortality after out-of-hospital cardiac arrest in a Spanish region.*  
  **PLOS One**, 12(4):e0175818, 2017.  
  DOI: https://doi.org/10.1371/journal.pone.0175818

- **Pediatric Brain Tumor**  
  Data informed by:  
  Stanić D., Grujičić D., Pekmezović T., Bokun J., Popović-Vuković M., Janić D., et al.  
  *Clinical profile, treatment and outcome of pediatric brain tumors in Serbia in a 10-year period: a national referral institution experience.*  
  **PLOS One**, 16(10):e0259095, 2021.  
  DOI: https://doi.org/10.1371/journal.pone.0259095

- **ColonRectal Cancer**  
  Data derived from:  
  Tai Y.-H., Chang W.-K., Wu H.-L., Chan M.-Y., Chen H.-H., Chang K.-Y.  
  *The effect of epidural analgesia on cancer progression in patients with stage IV colorectal cancer after primary tumor resection: a retrospective cohort study.*  
  **PLOS One**, 13(7):e0200893, 2018.  
  DOI: https://doi.org/10.1371/journal.pone.0200893

### Data Availability

The EHR datasets employed in this study are publicly available in the supplementary materials of the corresponding original publications under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. Direct access URLs are provided below:

- **Cardiac Arrest**:  
  https://figshare.com/articles/dataset/Mortality_after_out-of-hospital_cardiac_arrest_in_a_Spanish_Region/4876247?file=8166893

- **ColonRectal Cancer**:  
  https://figshare.com/articles/dataset/The_effect_of_epidural_analgesia_on_cancer_progression_in_patients_with_stage_IV_colorectal_cancer_after_primary_tumor_resection_A_retrospective_cohort_study/6846365?file=12464069

- **Type 1 Diabetes**:  
  https://figshare.com/articles/dataset/Circulating_osteocalcin_as_a_bone-derived_hormone_is_inversely_correlated_with_body_fat_in_patients_with_type_1_diabetes/8079389?file=15057092

- **Heart Failure & Depression**:  
  https://figshare.com/articles/dataset/Comorbid_Depression_and_Heart_Failure_A_Community_Cohort_Study/3916224?file=6130425

- **Neuroblastoma**:  
  https://doi.org/10.7717/peerj.5665/supp-5

- **Pediatric Brain Tumors**:  
  https://figshare.com/articles/dataset/Minimal_dataset_/16878192?file=31207500

- **Sepsis & SIRS**:  
  https://figshare.com/articles/dataset/_C_Reactive_Protein_and_Hemogram_Parameters_for_the_Non_Sepsis_Systemic_Inflammatory_Response_Syndrome_and_Sepsis_What_Do_They_Mean_/1644426?file=2637248

---

## Code Information

The repository includes:

- Python scripts for:
  - Synthetic data generation
  - Clustering with DBSCAN, HDBSCAN, and Mean-Shift
  - Computation of internal clustering validation metrics

The complete experimental pipeline is reproduced using the following notebook:

- `DBCV_paper_real.ipynb` – executes the full workflow, including data generation/loading, clustering, computation of all internal validation metrics, and reproduction of the figures and results reported in the manuscript.

Before running the notebook, please ensure that:
- all external tools are properly imported,
- all required dependencies listed in `requirements.txt` are installed.


---


## Methodology

### Clustering Algorithms

The following density-based clustering algorithms are used:

-DBSCAN

-HDBSCAN

-Mean-Shift

Default hyperparameters are used unless otherwise specified.
For validation, random hyperparameter configurations are also tested to assess metric robustness.

### Evaluation Method

The evaluation follows two complementary and independent validation approaches designed to assess the reliability of internal clustering validation metrics.

#### Synthetic Data Degradation Trends
Artificial datasets with well-defined cluster structures are progressively corrupted by adding increasing levels of noise. For each noise level, clustering is performed and internal validation metrics are computed.

A metric is considered reliable if its score consistently worsens as the underlying cluster structure degrades, reflecting the increasing difficulty of identifying meaningful density-based clusters.

#### Cross-Algorithm Consistency on Real-World Data
For each real-world medical dataset, clustering solutions are generated using three density-based clustering algorithms:
- DBSCAN
  
- HDBSCAN

- Mean-Shift

The agreement between clustering solutions is quantified using the **Adjusted Rand Index (ARI)**. Specifically, ARI values are computed pairwise between the clustering results of the three algorithms and then averaged.

Internal clustering validation metrics are evaluated by comparing their trends against the corresponding ARI trends. Metrics whose behavior is consistent with the ARI (i.e., improving when ARI improves and degrading when ARI degrades) are considered reliable indicators of clustering quality.

---

### Assessment Metrics

The following internal clustering validation metrics are evaluated in this study:

- **DBCV (Density-Based Clustering Validation)**: Measures cluster compactness and separation using mutual reachability distances derived from density connectivity.
- **AUCC (Area Under the Clustering Curve)**: Evaluates clustering quality through a pairwise ranking framework based on ROC analysis.
- **DISCO**: A density-connectivity-based, Silhouette-like metric with explicit handling of noise points.
- **LCCV (Local Cores-based Cluster Validity)**: A graph-based metric that evaluates clustering quality using representative local density cores.
- **CVDD (Clustering Validity based on Density Distribution)**: Combines neighborhood-based density estimation with graph-path distances to assess compactness and separation.
- **DBDBI (Density-Based Davies–Bouldin Index)**: A density-based variant of the classical Davies–Bouldin Index.
- **DBCHI (Density-Based Calinski–Harabasz Index)**: A density-based variant of the Calinski–Harabasz Index.
- **DBDI (Density-Based Dunn Index)**: A density-based variant of the Dunn Index.

Each metric is formally defined and mathematically explained in the Methods section of the manuscript.

# Contacts

Questions should be addressed to gsabino147@gmail.com (gsabino147(AT)gmail.com)
