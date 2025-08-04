# Explainable ADR Prediction for Pediatric Drugs

[📖 **Project overview & notebook walk-through (GitBook)**](https://htootayzaaung.gitbook.io/explainable-adr-prediction-for-pediatric-drugs/)

> The notebooks below were executed end-to-end in **Google Colab** and are provided here for review.  
> Running them locally will require downloading the data folder (link at the end) and updating path variables.

---

## Repository contents

| File | What it does |
|------|--------------|
| **CCLE_expression.ipynb** | Loads the full CCLE gene-expression matrix, selects the 753 COSMIC Cancer-Gene-Census transcripts, renames columns to gene symbols, and saves `CCLE_expression_cleaned.csv` for downstream joining. |
| **01_data_prep.ipynb** | Cleans the GDSC2 dose-response table, converts raw IC₅₀ values to natural-log scale, maps **COSMIC ID → DepMap ID** so cell-line names match CCLE, filters to drugs with valid SMILES strings, and writes three tidy CSVs covering compounds, cell lines, and activity labels. |
| **02_gen_dataset.ipynb** | Combines the cleaned IC₅₀ data with drug and cell-line metadata, builds long-format and pivoted tables for both **classification** (sensitive vs. resistant) and **regression** tasks, performs a stratified 60 / 20 / 20 train–validation–test split with fixed random seed, and saves the result under `datasets/sensitivity/…`. |
| **Data Integration & Preparation.ipynb** | Joins the sensitivity labels, the 735-gene expression profiles, and 2 048-bit Morgan fingerprints to create a **2 783-feature multimodal matrix** covering 108 696 drug–cell-line pairs, applies feature scaling, and exports the dataset as a 6.9 GB `.pkl` and a 1.6 GB `.csv`. |
| **Model Development & Training.ipynb** | Defines a dual-branch dense encoder (gene branch + chemical branch) with **8-head cross-modal attention**, trains the network on an A100 GPU using AdamW and mixed precision, logs metrics to TensorBoard, and saves `best_multimodal_model.keras` when validation AUROC peaks. |
| **Explainable AI-Driven ADR Prediction Report.pdf** | Technical report summarising biological motivation, data sources, model architecture, training procedure, performance metrics, and interpretability findings. |
| **My Notes.pdf** | Compact design diary that maps every raw file and notebook step, including bullet-point rationale and key parameter choices. |

---

## Data & artefacts

All raw tables, processed datasets (~7 GB total), the trained Keras model, and TensorBoard logs are available in this public Google Drive folder:


