# IDEA-RS temporal validation in the 2004 Pelotas Birth Cohort

Analysis code for the manuscript *Predicting adolescent depression across time: a within-population, decade-apart validation of the Identifying Depression Early in Adolescence Risk Score (IDEA-RS)*.

The script applies the published IDEA-RS model (Rocha et al., 2021) to adolescents from the 2004 Pelotas Birth Cohort and reproduces every analysis in the manuscript: the exclusion cascade, Tables 1 and 2, Figures 2 and 3, the sensitivity analyses, the attrition and missingness analyses, and Supplementary Tables S3 to S10 and Figures S1 to S5.

## Contents

- `idea_rs_validation_v12.qmd`: the complete analysis, in one Quarto document.

## Requirements

- R (4.4.0 was used) and [Quarto](https://quarto.org/).
- R packages: `dplyr`, `tidyr`, `purrr`, `haven`, `labelled`, `readr`, `tibble`, `ggplot2`, `pROC`, `patchwork`, `openxlsx`, `WeightedROC`.

The versions used in a given run are printed at the end of the output (`sessionInfo()`).

## Data

The data are not included in this repository because they are individual-level cohort data. Access is available on request through the cohort team (see the data availability statement in the manuscript and <https://epidemio-ufpel.org.br/coorte-2004/>).

To run the script, place these three files in a `data/` folder next to the script:

- `Banco_IDEA_RS_idalt.dta`
- `Banco_IDEA_RS_idalt2.dta`
- `pelotas_2004_com_mania_raw.dta`

## How to run

From the folder containing the script:

```
quarto render idea_rs_validation_v12.qmd
```

Alternatively, open the file in RStudio, set the working directory to the folder containing it, and run the R chunk. The analysis uses 2,000 bootstrap replicates per scenario and takes several minutes. Random seeds are fixed, so the results are reproducible.

## Outputs

Created when the script runs:

- `results/IDEA_RS_validation_results.xlsx`: one sheet per table (Tables 1 and 2, Tables S3 to S10, and supporting sheets).
- `results/figure_2_roc_curve.png`: Figure 2.
- `results/figure_3_calibration_*.png`: Figure 3 (original model, recalibrated model and combined).
- `results/figure_s1_flow_diagram.png`: Figure S1.
- `results/figure_s2_calibration_ipw.png`, `figure_s3_calibration_iq.png`, `figure_s4_calibration_dawba.png`, `figure_s5_calibration_sdq.png`: Figures S2 to S5.
- `results/calibration_all_scenarios.png`: all calibration plots in one figure.
- `data/derived/`: the analytic datasets (individual-level; do not share).

## Reference

Rocha, T. B.-M., Fisher, H. L., Caye, A., Anselmi, L., Arseneault, L., Barros, F. C., … Kieling, C. (2021). Identifying Adolescents at Risk for Depression: A Prediction Score Performance in Cohorts Based in 3 Different Continents. *Journal of the American Academy of Child and Adolescent Psychiatry, 60*(2), 262–273. https://doi.org/10.1016/j.jaac.2019.12.004
