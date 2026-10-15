# C. elegans RNAi Transcriptomics Analysis

Code extracted from a collaborative bioinformatics design project analyzing RNAi perturbation responses in *Caenorhabditis elegans* (GEO: GSE255865).

## Scope

- `preprocessing_worm.py`: load a genes-by-samples CSV matrix and metadata CSV (requires `sampleID`); generate QC plots and save `GSE255865_processed.h5ad`.
- `normalize.py`: normalize expression, select highly variable genes, run PCA, and save processed AnnData and figures.
- `scoring.py`: calculate Hotelling's T² scores for perturbation groups against a reference group.
- `cluster.py`: pseudo-bulk aggregation, correlation and hierarchical clustering.

## Installation

```bash
conda env create -f environment.yml
conda activate worm-rnai
```

## Preprocessing

```bash
python preprocessing_worm.py expression_matrix.csv metadata.csv
```

## Important limitations

This is a **code archive**, not a verified end-to-end executable pipeline. The source scripts were extracted from a broader team repository. In particular, the scoring output column names do not currently match those expected by `cluster.py`, and the downstream scripts may require metadata fields such as `variant` and `group` that the worm preprocessing script does not create automatically. Inputs, statistical assumptions, and integration must be checked before running the full workflow. No raw data are distributed here.

## Dataset

GEO accession: [GSE255865](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE255865).

## Attribution

Originally developed as part of a collaborative university design project. Please retain appropriate credit to all contributors when publishing or reusing the code. The original project's licensing and contributor permissions should be checked before public release.
