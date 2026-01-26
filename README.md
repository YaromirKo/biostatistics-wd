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

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

Yaromir Kobikov <kobikov.yaromir@gmail.com>

## Citation

---
