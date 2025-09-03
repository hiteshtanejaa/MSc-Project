# End-to-End Pipeline for Interpretable Cluster Analysis

**Author:** Hitesh Taneja
**Project for:** MSc Computer Science, University of Greenwich
**Supervisor:** Dr. Chris Walshaw
**Date:** September 2025

## 1. Overview

This project provides a universal, end-to-end Python pipeline for performing **interpretable cluster analysis** on high-dimensional data.

### The Problem: The "Black Box" Cluster

Standard clustering algorithms are effective at identifying groups in data but often produce a "black box" result. They assign labels like "Cluster 0" or "Cluster 1" without explaining *why* a data point belongs to a certain group. This makes it difficult for analysts and stakeholders to trust the results and derive actionable insights.

### The Solution: An Automated Interpretation Pipeline

This pipeline solves the "black box" problem by not only discovering clusters but also automatically generating a rich, multi-faceted, and human-readable explanation for them. It is designed to be robust, reusable, and applicable to any tabular dataset.

## 2. Key Features

* **Universal & Configurable:** Easily adaptable to any dataset by modifying a simple `CONFIG` dictionary. No code changes are required.

* **Automated Preprocessing:** Automatically detects numerical and categorical features and applies appropriate imputation, scaling, and encoding.

* **Data-Driven Methodology:**

  * Uses a data-driven approach to select the best DR algorithm (UMAP/t-SNE) based on dataset size.

  * Automatically determines the optimal number of clusters (`k`) using the Elbow Method.

* **Multi-Faceted Interpretation Module:** Provides four complementary explanations for the discovered clusters:

  1. **Centroid Profile:** The statistical "average" of a cluster.

  2. **Medoid Prototype:** The single best *real-world example* from the dataset.

  3. **Decision Tree Surrogate:** A set of simple, human-readable rules that define the clusters.

  4. **SHAP Analysis:** A clear ranking of the features that were most important in separating the clusters.

## 3. Pipeline Architecture

The system is designed as a sequential, 4-stage pipeline:

1. **Configuration & Data Ingestion:** The user defines the dataset path and parameters.

2. **Automated Preprocessing:** The data is cleaned, scaled, and encoded.

3. **Core Analysis Engine:** Dimensionality reduction and clustering are performed.

4. **Interpretation & Reporting:** Quantitative metrics and qualitative explanations are generated.

## 4. Tech Stack

* **Language:** Python

* **Core Libraries:** Scikit-learn, Pandas, NumPy

* **Dimensionality Reduction:** UMAP, t-SNE

* **Clustering & Interpretation:** k-means, SHAP, Decision Trees

* **Visualization:** Matplotlib, Seaborn

## 5. How to Use

#### Prerequisites

Ensure you have the required Python libraries installed:

```pip install pandas scikit-learn umap-learn matplotlib seaborn shap```

#### Steps

1. **Clone the Repository:**
   `git clone "https://github.com/hiteshtanejaa/MSc-Project.git"`
   `cd MSc-Project`
   
2. **Configure the Pipeline:**
Open the `pipeline_integration.py` script and modify the `CONFIG` dictionary at the top to point to your dataset.

**Example for the Forest Cover Type dataset:**

```
CONFIG = {
"file_path": "file.csv",
"target_column": "Cover_Type",
"id_column": None,
"features_to_drop": []
}
```

3. **Run the Script:**
Execute the pipeline from your terminal
`python Final_pipeline.py`

4. **View the Results:**
The script will print all quantitative metrics and qualitative interpretations to the console and display the Elbow Method plot, the final UMAP scatter plot, and the SHAP summary plot.

## 6. Validation

The pipeline's robustness was validated on five diverse, high-dimensional datasets:

* Titanic (Demographics)

* PISA 2018 (Social Science)

* Forest Cover Type (Ecology, >580k samples)

* Gene Expression Cancer RNA-Seq (Bioinformatics, >20k features)

* MNIST (Computer Vision, >70k samples)

Across all datasets, the pipeline successfully identified and explained meaningful clusters, demonstrating its effectiveness and universality.

## 7. Future Work

The next logical step for this project is to formally package this tool for distribution on the Python Package Index (PyPI), making it easily installable and accessible to the wider data science community.

