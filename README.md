# C. elegans RNAi Transcriptomics Analysis

An analysis codebase extracted from a collaborative university design project studying RNAi perturbation responses in *Caenorhabditis elegans* (GEO: [GSE255865](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE255865)).

## Scripts and workflow

1. `preprocessing_worm.py`: read a genes × samples CSV expression matrix and a metadata CSV with `sampleID` and `group` or `variant` columns; run QC and create `GSE255865_processed.h5ad`. Missing `group`/`variant` is copied from the one provided.
2. `normalize.py`: library-size normalization, log1p, highly variable genes, PCA and diagnostic plots.
3. `scoring.py`: compare RNAi conditions against a control using Hotelling's T², writing `variant,HotellingT2` to CSV. Groups with inadequate sample size are skipped.
4. `cluster.py`: group-mean expression (pseudo-bulk-like aggregation), Spearman correlation, hierarchical clustering and dendrograms.

## Installation

```bash
conda env create -f environment.yml
conda activate worm-rnai
```

## Example commands

```bash
python preprocessing_worm.py expression_matrix.csv metadata.csv
python normalize.py GSE255865_processed.h5ad qc_figures normalized.h5ad
python scoring.py normalized.h5ad x.vector qc_figures scores.csv
python cluster.py normalized.h5ad scores.csv
```

Replace `x.vector` with the actual control label in your metadata. The preprocessing script assumes rows are genes and columns are samples. Provide raw nonnegative count-like data, not previously log-transformed values.

## Validation status and scientific caveats

**Interfaces have been aligned, but this workflow has not yet been end-to-end tested against the real GSE255865 data.** Actual input column names, normalization choices, PCA dimensionality, sample counts and statistical assumptions must be checked. In particular, Hotelling's T² requires enough biological replicates relative to the number of principal components and an appropriate covariance model. Samples are biological experiment samples, not single cells; the group mean is not a count-summing single-cell pseudobulk. The current clustering and scoring outputs are exploratory and do not establish differential expression significance or causal effects. No raw data are distributed here.

## Attribution

Developed originally as part of a collaborative university design project. Credit should be given to the team contributors. Verify the source project's license and contributors' permissions before redistributing code.
