# ALCHEMIST TME Analysis

Unsupervised clustering and statistical framework for large-scale tumor microenvironment characterization, applied to 1,176 early-stage NSCLC patients from the NCI ALCHEMIST trial.

## Paper

Baker E, Mehaffy N. "Unsupervised clustering and statistical framework for large-scale tumor microenvironment characterization: Application to early-stage non-small cell lung cancer from the ALCHEMIST trial." *Computers in Biology and Medicine* (2026). [Under Review]

## Data

All data are publicly available from the [NCI Genomic Data Commons](https://portal.gdc.cancer.gov), project ALCHEMIST-ALCH, Data Release 45.0 (December 4, 2025).

- **Clinical data:** `clinical.tsv` (1,176 cases)
- **Biospecimen data:** `slide.tsv` (1,218 slides with TME data), `sample.tsv` (tumor descriptors)

## Pipeline

| Module | Method | Purpose |
|--------|--------|---------|
| 1 | Mann-Whitney U / Kruskal-Wallis | Nonparametric association testing (59 tests) |
| 2 | Benjamini-Hochberg FDR | Family-wise multiple testing correction |
| 3 | Spearman rank correlation | Coordinated immune infiltration patterns |
| 4 | K-means (silhouette-optimized) | Unsupervised TME subtype discovery (k=6) |

## Key Findings

- **17/59 tests significant** after FDR correction (28.8% discovery rate)
- Histological TME divergence confined to necrosis (q=1.5×10⁻²⁸) and neutrophils (q=1.3×10⁻³); lymphocytes equivalent (q=0.69)
- Coordinated immune co-infiltration: monocyte-neutrophil ρ=0.62, lymphocyte-monocyte ρ=0.55
- Six TME subtypes identified, including necrotic subtype with 2.4× squamous enrichment
- Recurrent tumors show normal cell depletion (q=4.0×10⁻⁷) with preserved immune infiltration (q=0.71)

## Usage

The analysis runs on [Kaggle](https://www.kaggle.com). Upload `ALCHEMIST_TME_Analysis.ipynb` and link the ALCHEMIST clinical and biospecimen datasets.

### Requirements
- Python 3.10+
- pandas, numpy, scipy, scikit-learn, statsmodels, matplotlib, seaborn

## Repository Structure

```
├── ALCHEMIST_TME_Analysis.ipynb    # Complete analysis pipeline
├── README.md                        # This file
└── figures/
    ├── fig1_tme_by_histology.png
    ├── fig2_tme_correlations.png
    ├── fig3_primary_vs_recurrent.png
    ├── fig4_tme_clusters.png
    └── fig5_immune_status.png
```

## License

This project uses publicly available data from the NCI GDC under their [data use agreement](https://gdc.cancer.gov/access-data/data-access-processes-and-tools).

## Citation

If you use this pipeline or findings, please cite:

```
Baker E, Mehaffy N. Unsupervised clustering and statistical framework for
large-scale tumor microenvironment characterization: Application to early-stage
non-small cell lung cancer from the ALCHEMIST trial. Comput Biol Med. 2026.
```
