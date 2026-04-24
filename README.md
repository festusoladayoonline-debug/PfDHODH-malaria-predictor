
***

# Computational Drug Discovery Pipeline for PfDHODH Inhibitors
### A Quantitative Structure-Activity Relationship (QSAR) Study for Antimalarial Lead Identification

![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)
![RDKit](https://img.shields.io/badge/Library-RDKit-green.svg)
![Scikit-Learn](https://img.shields.io/badge/ML-Scikit--Learn-orange.svg)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen.svg)

## 📝 Abstract
This project presents an end-to-end computational drug discovery pipeline targeting **Plasmodium falciparum Dihydroorotate dehydrogenase (PfDHODH)**, a critical enzyme for the parasite’s survival. Using a curated dataset of 369 bioactive compounds from the **ChEMBL database**, we implemented an automated 9-phase workflow covering data acquisition, feature engineering, and predictive modeling. 

The research achieved high predictive accuracy, notably with a **Support Vector Regression (SVR)** model attaining an **R² value > 0.70**. Compounds were characterized using 2048-bit Morgan fingerprints and 17 physicochemical descriptors to classify bioactivity into active, intermediate, and inactive categories. The final model is deployed via a **Streamlit web application**, providing a real-time interface for bioactivity prediction and drug-likeness screening.

---

## 🧬 Biological Background
**PfDHODH** is a mitochondrial enzyme essential for *de novo* pyrimidine biosynthesis in *Plasmodium falciparum*. Because the parasite lacks a pyrimidine salvage pathway (unlike human cells), inhibiting this enzyme is a validated strategy for selective antimalarial toxicity with minimal side effects.

---

## 🚀 Workflow Pipeline
The pipeline is integrated into a single, ready-to-run notebook consisting of the following phases:

1.  **Data Acquisition**: Automated retrieval of PfDHODH bioactivity data (Target ID: `CHEMBL3486`) via the ChEMBL REST API.
2.  **Preprocessing & Classification**: Data cleaning and classification into Active (IC50 ≤ 1,000 nM), Intermediate, and Inactive (IC50 > 10,000 nM).
3.  **pIC50 Transformation**: Normalizing bioactivity data using the negative decadic logarithm of IC50 (Molar).
4.  **Molecular Descriptor Calculation**: Generating Lipinski parameters and 2048-bit Morgan Fingerprints using RDKit.
5.  **Exploratory Data Analysis (EDA)**: Visualizing chemical space and feature correlations.
6.  **Regression Modeling**: Implementation and hyperparameter optimization of Random Forest, Gradient Boosting, SVR, and Ridge Regression.
7.  **Binary Classification**: Identifying potential hits through classification algorithms.
8.  **Validation & Interpretation**: Evaluating models via 5-fold cross-validation, RMSE, and R² metrics.
9.  **Deployment**: Exporting trained models for use in the Streamlit web application.

---

## 🛠️ Requirements & Installation
This project requires **Python 3.11+** and the following core libraries:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn rdkit requests
```

### Setup
1. Clone the repository.
2. Ensure you have an active internet connection for the ChEMBL API request (Phase 1) or provide the local CSV.
3. Run the notebook `Tutorial-Malaria.ipynb` from top to bottom.

---

## 📊 Key Results
* **Dataset Size**: 369 high-quality bioactive compounds.
* **Bioactivity Range**: pIC50 values from **3.06 to 8.22**.
* **Best Model**: Support Vector Regression (SVR) with **R² > 0.70**.
* **Feature Engineering**: Successfully utilized a combination of 1D/2D physicochemical descriptors and circular fingerprints.


---

## 🌐 Deployment: Streamlit App
The trained models are exported to the `PfDHODH_deployment_models` folder. These can be used to power a web application that allows users to:
* Input molecular SMILES strings.
* Predict pIC50 and bioactivity class.
* Verify Lipinski's "Rule of Five" compliance.

---

## 🎓 Acknowledgments
* **Author**: Festus Ogungbemiro
* **Institution**: CBIOS - Universidade Lusófona, BioNatural and Computational Chemistry Research Group, Lisbon, Portugal
* **Context**: Presented as a tutorial project at CADD 2.0
* **Data Source**: [ChEMBL Database](https://www.ebi.ac.uk/chembl/)

---

## 📜 License
This project is intended for educational and research purposes. Please cite the author and institution if using this pipeline in your work.
