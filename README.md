# gut_microbiome_crc_age_project 
# From Diversity to Prediction: Gut Microbiome Signatures of Colorectal Cancer and Ageing

This project reframes my Human Microbiome Data Science assignment as a single portfolio-style study on how gut microbiome composition relates to colorectal cancer (CRC) status and host age. It consolidates alpha diversity interpretation, beta diversity analysis, PERMANOVA testing, supervised classification, and regression-based age prediction into one narrative.

## Project Summary

The analysis is based on the Yachida et al. 2019 gut microbiome dataset used in the assignment. The project examines three connected questions:

1. Do CRC and control samples differ in alpha and beta diversity?
2. Can machine learning models classify CRC versus control from species-level abundance profiles?
3. Can microbiome composition be used to predict chronological age?

## Analytical Scope

- Alpha diversity comparison of CRC versus control using Shannon diversity and Pielou's evenness, interpreted with a Wilcoxon rank-sum framework from the submitted report.
- Beta diversity analysis using Bray-Curtis dissimilarity after total-sum scaling (TSS) normalization.
- PERMANOVA testing for the effects of `disease_condition`, `age`, and their joint contribution to gut microbiome variation.
- PCoA visualization of CRC versus control separation in ordination space.
- CRC classification using Random Forest and XGBoost after sparse-feature filtering and CLR transformation.
- Age prediction using feature-selected linear regression on normalized taxa abundances.

## Key Results

### 1. Diversity patterns

- Alpha diversity showed only subtle differences between CRC and control groups, with substantial overlap between distributions.
- Beta diversity analysis suggested statistically significant but small shifts in microbiome composition associated with disease status and age.

### 2. PERMANOVA findings

| Test | Result |
| --- | --- |
| Disease condition only | `F = 2.23`, `R^2 = 0.00443`, `p = 0.005` |
| Age only | `F = 4.98`, `R^2 = 0.00982`, `p = 0.001` |
| Disease condition + age | `F = 3.63`, `R^2 = 0.01427`, `p = 0.001` |

Interpretation: both CRC status and age significantly influence gut microbiome structure, but the effect sizes are small, which suggests that other biological or environmental factors also shape the community.

### 3. CRC classification performance

- Random Forest accuracy: `0.70`
- XGBoost accuracy: `0.65-0.66`
- Random Forest AUC: `0.766`
- XGBoost AUC: `0.760`

Random Forest performed slightly better than XGBoost and produced the strongest signal for taxa ranking.

Top taxa highlighted by the Random Forest model:

- `Gemella_morbillorum`
- `Roseburia_faecis`
- `Parvimonas_micra`
- `Holdemania_filiformis`
- `Peptostreptococcus_stomatis`

Directionality from the original interpretation suggested that `Roseburia_faecis` was relatively higher in controls, while the other leading taxa were relatively higher in CRC samples.

### 4. Age prediction performance

- Feature-selected linear regression MAE: `9.02 years`
- Pearson correlation: `r = 0.1966`
- P-value: `0.027391`
- Retained features: `87`

The regression model improved strongly over the unfiltered baseline but still captured only a weak age-related signal, indicating that microbiome composition alone is not sufficient for highly accurate chronological age prediction.

## Included Files

- `gut_microbiome_crc_project_combined.ipynb`: consolidated notebook report with methods, code, plots, and interpretations.
- `README.md`: complete project documentation.
- `Resume_Kalpesh_IIITD_updated.docx`: updated resume with this project added.
- `pcoa_crc_vs_control.png`: beta diversity ordination figure.
- `age_prediction_regression.png`: actual versus predicted age regression figure.

## Data Requirements

The original assignment files reference dataset tables such as:

- `YachidaS_2019_Metadata.csv`
- `YachidaS_2019_SpeciesProfile.csv`

These source datasets were not bundled in the provided files, so the combined notebook is presented as a polished project report with reusable code blocks rather than a fully rerunnable package.

## Tools and Methods

- R: `vegan`, `ggplot2`
- Python: `pandas`, `matplotlib`, `scikit-learn`, `scipy`, `xgboost`, `scikit-bio`
- Statistics: Wilcoxon rank-sum test, Bray-Curtis dissimilarity, PERMANOVA, Pearson correlation
- Machine learning: Random Forest, XGBoost, feature-selected Linear Regression

## Portfolio-Ready Description

From Diversity to Prediction: Gut Microbiome Signatures of Colorectal Cancer and Ageing presents an end-to-end microbiome analytics workflow that moves from ecological diversity assessment to predictive modeling. The project shows how gut microbial communities differ subtly but significantly between CRC and control samples, demonstrates how machine learning can identify CRC-associated taxa, and evaluates the limits of microbiome-only age prediction.

## Notes

- The alpha-diversity interpretation was reconstructed from the submitted assignment PDF because standalone source code and plot image files for Question 1 were not provided.
- The notebook consolidates cleaned versions of the original R and Python workflows along with the written interpretations from the assignment materials.
