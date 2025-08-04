# Explainable ADR Prediction for Pediatric Drugs

[📖 **Full project documentation on GitBook**](https://htootayzaaung.gitbook.io/explainable-adr-prediction-for-pediatric-drugs/)

> The notebooks in this repository are **review-only** and were executed end-to-end in Google Colab.

## Repository contents

| File | Description |
|------|-------------|
| **CCLE_expression.ipynb** | Loads CCLE matrix (1 406 × 19 221), filters to 753 COSMIC genes, saves **CCLE_expression_cleaned.csv** |
| **01_data_prep.ipynb** | Cleans GDSC2 IC50 tables, maps **COSMIC → DepMap** IDs, writes three tidy CSVs |
| **02_gen_dataset.ipynb** | Generates stacked & pivoted classification/regression tables and stratified splits |
| **Data Integration & Preparation.ipynb** | Builds the **2 783-feature multimodal matrix (108 696 rows)**; exports 6.9 GB `.pkl` & 1.6 GB `.csv` |
| **Model Development & Training.ipynb** | Trains a dual-branch encoder with 8-head cross-modal attention; saves **best_multimodal_model.keras** |
| **Explainable AI-Driven ADR Prediction Report.pdf** | 43-page technical report |
| **My Notes.pdf** | Design diary & notebook summaries |

## Data & artefacts

All raw tables, processed datasets (~7 GB) and the saved model are available in this public Drive folder:

