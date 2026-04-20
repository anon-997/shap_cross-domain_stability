# SHAP Cross-Domain Stability

## Reproduce Results

pip install -r requirements.txt

python code/pipeline.py

## Outputs
- CSV tables → results/
- Figures → figures/

## Notes
- Uses fixed pretrained models (DistilBERT + Afriberta/XLM-R fallback)
- SHAP computed on sampled subsets
- Seed = 42
