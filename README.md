# SHAP Cross-Domain Stability for Sentiment Classification

This repository contains the code and exported artifacts used to evaluate the cross-domain stability of SHAP explanations for sentiment classification. The experiments compare explanation behavior across multiple sentiment datasets and report predictive performance, cross-domain stability, and within-domain stability results.

## Repository Structure

- `code/pipeline.py`  
  End-to-end script for dataset loading, preprocessing, model inference, SHAP computation, aggregation, stability analysis, and figure generation.

- `results/`  
  Exported CSV files used for analysis and reporting.

- `figures/`  
  Generated figures used in the paper.

- `requirements.txt`  
  Python dependencies required to run the pipeline.

## Included Results

The repository includes the following main result files:

- `final_results_table.csv`  
  Combined summary table of predictive and stability results.

- `predictive_metrics_with_ci.csv`  
  Accuracy and macro-F1 with bootstrap confidence intervals.

- `jaccard_k_full_small.csv`  
  Cross-domain top-k token overlap results.

- `spearman_full_small.csv`  
  Cross-domain rank-correlation results over shared tokens.

- `split_half_stability_full_small.csv`  
  Within-domain split-half stability results.

- `predictions_all_datasets.csv`  
  Model predictions across the evaluated datasets.

## Included Figures

The repository includes the following generated figures:

- `figure_accuracy_ci.png`
- `figure_jaccard20_heatmap.png`
- `figure_jaccard_k_lines.png`
- `figure_within_vs_cross_jaccard.png`
- `figure_split_half_stability.png`

## Experimental Pipeline

The pipeline follows these main steps:

1. Load English and African sentiment datasets.
2. Standardize dataset schemas into a common format.
3. Harmonize labels into binary sentiment classes.
4. Create balanced evaluation subsets.
5. Run inference using fixed pretrained sentiment classifiers.
6. Compute predictive metrics and bootstrap confidence intervals.
7. Sample subsets for SHAP analysis.
8. Compute token-level SHAP values and save outputs incrementally.
9. Aggregate global token importance scores.
10. Compute explanation stability using Jaccard overlap, Spearman correlation, and split-half stability.
11. Export result tables and figures.

## Models

The experiments use the following pretrained models:

- distilbert-base-uncased-finetuned-sst-2-english
- Davlan/naija-twitter-sentiment-afriberta-large
- cardiffnlp/twitter-xlm-roberta-base-sentiment-multilingual (fallback)

## Reproducing the Results

### 1. Install dependencies

pip install -r requirements.txt

### 2. Run the full pipeline

python code/pipeline.py

## Output Locations

- CSV result tables → results/
- Figures → figures/

## Reproducibility Notes

- Random seed = 42
- Balanced evaluation subsets
- SHAP computed on sampled data for efficiency
- SHAP stage is the main runtime cost

## Purpose

This repository supports reproducibility of experiments and findings on cross-domain explanation stability. All CSVs and figures are direct outputs from the pipeline.
