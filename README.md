# Explainable ADR Prediction for Pediatric Drugs

[📖 **Project overview & notebook walk-through (GitBook)**](https://htootayzaaung.gitbook.io/explainable-adr-prediction-for-pediatric-drugs/)

> These notebooks were executed end-to-end in **Google Colab** and are provided here for review.  
> To run them locally you’d need to download the data folder (link below) and update the paths.

---

## Repository contents

| File | Description |
|------|-------------|
| **CCLE_expression.ipynb** | Loads the full CCLE expression matrix (1,406 cell lines × 19,221 transcripts), filters to the 753 COSMIC Cancer-Gene-Census genes, renames columns to gene symbols, and saves `CCLE_expression_cleaned.csv` for downstream merging. |
| **01_data_prep.ipynb** | Cleans the GDSC2 dose-response table, converts raw IC₅₀ values to natural-log scale, maps **COSMIC ID → DepMap ID** so cell-line names align with CCLE, drops drugs without valid SMILES strings, and outputs three tidy CSVs covering compounds, cell lines, and activity labels. |
| **02_gen_dataset.ipynb** | Merges the cleaned IC₅₀ data with compound and cell-line metadata, produces both **classification** (sensitive vs resistant) and **regression** (ln IC₅₀) tables, performs a stratified 60 / 20 / 20 train–validation–test split, and saves the CSVs under `datasets/sensitivity/…`. |
| **Data Integration & Preparation.ipynb** | Combines the activity labels, the 735-gene expression profiles, and 2,048-bit Morgan fingerprints to form a **2,783-feature multimodal matrix** covering 108,696 drug–cell-line pairs, applies feature scaling, and exports the dataset as a 6.9 GB `.pkl` and a 1.6 GB `.csv`. |
| **Model Development & Training.ipynb** | Builds a dual-branch dense encoder with **8-head cross-modal attention**, trains on an NVIDIA A100 (AdamW, mixed precision), logs metrics to TensorBoard, and saves `best_multimodal_model.keras`. |
| **Explainable AI-Driven ADR Prediction Report.pdf** | Technical report summarising biological motivation, data pipeline, model architecture, performance metrics, and interpretability findings. |
| **My Notes.pdf** | Design diary that maps every raw file to each notebook step and summarises key parameter choices. |

---

## Data & artefacts

All raw tables, processed datasets (~7 GB total), the trained model, and TensorBoard logs are available in this public Google Drive folder: https://drive.google.com/drive/folders/1QlwU7aKmkV76GLZCNLw1hn67PVubw-R3

