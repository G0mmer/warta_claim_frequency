# Motor insurance claim-frequency prediction — Warta competition

Report from a student data science competition organized by Warta TUiR. The task was to rank renewing motor third-party liability insurance policies by expected claim frequency, using anonymized historical data supplied by the organizer.

**Team:** Bartosz Eppel, Mateusz Gonera, Jakub Marczak.

**Result:** first place in the competition, with an organizer-reported normalized Gini of **25.22%** on the hidden test set.

[Read the project report](report.pdf)

## Approach

- Built features from policy and claims history for a main table of 491,229 policy records.
- Used 565 features and an ensemble of 15 Poisson LightGBM models, with Optuna tuning and five-fold cross-validation across three seeds.
- Used out-of-fold target encoding and averaged percentile ranks of model outputs.
- Excluded target-period exposure from predictors after identifying leakage; handled it as an offset in the Poisson model.

## My main contribution

- Built predictors from the claims-history table.
- Designed experiments comparing classification and Poisson objectives.
- Proposed rank-based prediction averaging and aggregation across random seeds.
- Checked training and scoring feature distributions with Kolmogorov-Smirnov statistics.


The competition result belongs to the team. This report describes a notebook-based proof of concept, not a deployed insurance pricing system. Normalized Gini evaluates ranking rather than probability calibration.

## Repository contents

This repository contains the report and a project summary. The training data and model implementation are not included, as the competition took place on the closed orgnizer's enviroment. The report describes validation choices and limitations; performance on future policy periods was not established by the competition.
