# Biostatistics WD - Postural Asymmetry and SF Analysis

A comprehensive R-based biostatistics project for analyzing postural asymmetry (PA) measurements in rats, with a focus on withdrawal (WD) studies using Bayesian statistical frameworks.

## Project Overview

This project provides tools and analyses for studying postural asymmetry in laboratory rats, particularly in the context of withdrawal studies. The analysis employs Bayesian statistical methods through R/brms interface to Stan, enabling robust statistical inference with credible intervals and posterior distributions.

## Features

- **Bayesian Statistical Analysis**: Uses R/brms interface to Stan for robust statistical modeling
- **Postural Asymmetry Metrics**: Analysis of MPA (Magnitude of Postural Asymmetry) and PAS measurements
- **Force Measurement Analysis**: Processing and analysis of force measurement data
- **Reproducible Reports**: R Markdown reports with embedded statistical analysis
- **Publication-Ready Figures**: Generates editable vector figures for PowerPoint presentations
- **P-value Estimation**: Uses emmeans for statistical comparisons with multiple testing corrections

## Project Structure

```
biostatistics-wd/
├── BayesianPValue.R          # Core functions and setup for Bayesian analysis
├── data/                     # Raw data files
│   ├── PAdata-forSTAT-20240513-HW.xlsx
│   ├── WD_PA 25 12 26_1.xlsx
│   └── Force-WD-20240513/
├── 1_task_mpa_pas_pa/        # Task 1: MPA, PAS, and PA analysis vs control
├── 2_task_mpa_pas/           # Task 2: MPA and PAS with treatments (SSR, Conivaptan)
├── 3_task_mpa_pas/           # Task 3: Additional MPA and PAS analyses
├── force_measurement/        # Force measurement analysis and preprocessing
├── rds/                      # R data objects for reproducible analysis
└── results/                  # Generated reports and figures
```

## Key Measurements

- **MPA (Magnitude of Postural Asymmetry)**: Quantifies the degree of postural imbalance
- **PAS (Postural Asymmetry Score)**: Alternative scoring method for postural asymmetry
- **Pa (Postural Asymmetry)**: Probability of postural asymmetry measurements
- **Force Measurements**: Biomechanical force analysis related to postural control

## Dependencies

The project requires the following R packages:

### Core Analysis
- `tidyverse` - Data manipulation and visualization
- `brms` - Bayesian regression modeling via Stan
- `rstan` - R interface to Stan
- `emmeans` - Estimated marginal means and contrasts
- `tidybayes` - Bayesian analysis utilities

### Data Import/Export
- `readxl` - Excel file import
- `openxlsx` - Excel file export

### Visualization
- `ggplot2` (via tidyverse) - Base plotting
- `ggstance`, `ggridges` - Specialized plot types
- `cowplot`, `patchwork` - Plot composition
- `viridis`, `ggsci`, `RColorBrewer` - Color palettes

### Reporting
- `officer` - PowerPoint and Word document generation
- `rvg` - Vector graphics for Office documents
- `flextable` - Formatted tables for reports
- `latex2exp` - LaTeX expressions in plots

## Getting Started

1. **Setup Environment**
   ```r
   source("BayesianPValue.R")
   ```

2. **Configure Stan**
   The project automatically configures Stan for optimal performance:
   - Uses available CPU cores minus one
   - Auto-writes compiled models
   - Sets up parallel processing

3. **Run Analysis**
   Navigate to the relevant task directory and knit the R Markdown reports:
   ```r
   # Example: Task 1 MPA analysis
   rmarkdown::render("1_task_mpa_pas_pa/report_MPA_wd_vs_control.Rmd")
   ```

## Analysis Workflow

1. **Data Import**: Excel files are read and cleaned using tidyverse functions
2. **Bayesian Modeling**: Statistical models are fit using brms with appropriate priors
3. **Posterior Analysis**: Results are summarized using median and HDI (Highest Density Intervals)
4. **Visualization**: Publication-ready plots are generated with uncertainty visualization
5. **Statistical Testing**: P-values and contrasts are computed using emmeans with multiple testing corrections

## Key Functions

- `emm_show()`: Display formatted emmeans results with significance highlighting
- `my.stat_eye()`: Generate eye plots for posterior distributions
- `signif.num()`: Add significance stars to p-values
- `notify()`: System notification when analyses complete

## Statistical Approach

The project uses a Bayesian framework that provides:
- **Credible Intervals**: 95% HDI for parameter estimates
- **Posterior Distributions**: Full uncertainty quantification
- **Multiple Comparisons**: Adjusted using multivariate t-distribution
- **Effect Sizes**: Meaningful magnitude assessment beyond p-values

## Output

- **Word Documents**: Formatted reports with tables and figures
- **PowerPoint Files**: Editable vector graphics for presentations
- **RDS Files**: Cached R objects for reproducible analysis

## Session Info

```text
R version 4.5.2 (2025-10-31)
Platform: aarch64-apple-darwin20
Running under: macOS Tahoe 26.6.2

Matrix products: default
BLAS:   /System/Library/Frameworks/Accelerate.framework/Versions/A/Frameworks/vecLib.framework/Versions/A/libBLAS.dylib
LAPACK: /Library/Frameworks/R.framework/Versions/4.5-arm64/Resources/lib/libRlapack.dylib;  LAPACK version 3.12.1

locale:
[1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

time zone: Asia/Tashkent
tzcode source: internal

attached base packages:
[1] stats     graphics  grDevices utils     datasets  methods   base

other attached packages:
 [1] processx_3.8.6      RColorBrewer_1.1-3  ggsci_4.2.0         viridis_0.6.5
 [5] viridisLite_0.4.2   flextable_0.9.10    emmeans_2.0.1       brms_2.23.0
 [9] Rcpp_1.1.1          rstan_2.32.7        StanHeaders_2.32.10 latex2exp_0.9.8
[13] patchwork_1.3.2     cowplot_1.2.0       ggridges_0.5.7      ggstance_0.3.7
[17] tidybayes_3.0.7     modelr_0.1.11       rvg_0.4.0           officer_0.7.2
[21] openxlsx_4.2.8.1    readxl_1.4.5        lubridate_1.9.4     forcats_1.0.1
[25] stringr_1.6.0       dplyr_1.1.4         purrr_1.2.1         readr_2.1.6
[29] tidyr_1.3.2         tibble_3.3.1        ggplot2_4.0.1       tidyverse_2.0.0

loaded via a namespace (and not attached):
 [1] gridExtra_2.3           inline_0.3.21           rlang_1.1.7
 [4] magrittr_2.0.4          matrixStats_1.5.0       compiler_4.5.2
 [7] loo_2.9.0               systemfonts_1.3.1       vctrs_0.6.5
[10] pkgconfig_2.0.3         arrayhelpers_1.1-0      fastmap_1.2.0
[13] backports_1.5.0         rmarkdown_2.30          tzdb_0.5.0
[16] ps_1.9.1                ragg_1.5.0              xfun_0.55
[19] uuid_1.2-1              broom_1.0.11            parallel_4.5.2
[22] R6_2.6.1                stringi_1.8.7           cellranger_1.1.0
[25] estimability_1.5.1      knitr_1.51              bayesplot_1.15.0
[28] Matrix_1.7-4            timechange_0.3.0        tidyselect_1.2.1
[31] rstudioapi_0.17.1       abind_1.4-8             yaml_2.3.12
[34] codetools_0.2-20        pkgbuild_1.4.8          lattice_0.22-7
[37] withr_3.0.2             bridgesampling_1.2-1    S7_0.2.1
[40] askpass_1.2.1           posterior_1.6.1         coda_0.19-4.1
[43] evaluate_1.0.5          RcppParallel_5.1.11-1   zip_2.3.3
[46] ggdist_3.3.3            xml2_1.5.1              pillar_1.11.1
[49] tensorA_0.36.2.1        checkmate_2.3.3         stats4_4.5.2
[52] distributional_0.5.0    generics_0.1.4          hms_1.1.4
[55] rstantools_2.6.0        scales_1.4.0            glue_1.8.0
[58] gdtools_0.4.4           tools_4.5.2             data.table_1.18.0
[61] mvtnorm_1.3-3           grid_4.5.2              QuickJSR_1.8.1
[64] nlme_3.1-168            cli_3.6.5               textshaping_1.0.4
[67] fontBitstreamVera_0.1.1 svUnit_1.0.8            Brobdingnag_1.2-9
[70] gtable_0.3.6            digest_0.6.39           fontquiver_0.2.1
[73] farver_2.1.2            htmltools_0.5.9         lifecycle_1.0.5
[76] fontLiberation_0.1.0    openssl_2.3.4
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

Yaromir Kobikov <kobikov.yaromir@gmail.com>

## Citation

---
