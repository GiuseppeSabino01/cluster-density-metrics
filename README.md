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

- Neuroblastoma
- Type 1 Diabetes
- Sepsis & SIRS
- Heart Failure & Depression
- Cardiac Arrest
- Pediatric Brain Tumor
- ColonRectal Cancer

Due to privacy and licensing constraints, **raw medical datasets are not redistributed** in this repository.  

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

