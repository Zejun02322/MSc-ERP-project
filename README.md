# MSc-ERP-project
Code and supplementary materials for my MSc Data Science dissertation at the University of Manchester.

## Project title
Comparison of Bayesian Regression Model Covariates for Predicting Asymptomatic COVID-19 Infection from Activity Diary Data.

## Project overview
This project investigates alternative representations of social exposure for predicting asymptomatic COVID-19 infection using participant-level activity diary data from a UK university cohort.

The analysis addresses three research questions:

1. Which of four candidate exposure measures (binary participation, contact count, duration, and contact-time product) receives the strongest support for modelling infection status?
2. Does the association between the best supported exposure indicators and infection status vary depending on activity settings, and does a specific setting model receive greater support than pooled model?
3. Does household contact-time provide additional information beyond the best-supported non-household exposure model?

Bayesian logistic regression models were fitted in Stan and compared using marginal likelihoods, Bayes factors, posterior model probabilities, and Pareto-smoothed importance sampling leave-one-out cross-validation (PSIS-LOO).

## Requirements
R 4.5.1. Packages: rstan, bridgesampling, loo, bayesplot, tidyverse, scales, ggcorrplot, patchwork.

```r
install.packages(c("rstan", "bridgesampling", "loo", "tidyverse",
                   "scales", "ggcorrplot", "patchwork"))
```
                   
The data file data/bht_IndividualsData.csv is included.


## How to run
Set the working directory to the repository root, then run the three scripts **in order**:

```r
source("R/01_data_validation_and_eda.R")
source("R/02_RQ1_exposure_metric_comparison.R")
source("R/03_RQ2_RQ3_duration_household.R")
```

`R/00_setup.R` is not run on its own; each script loads it automatically.

The order matters. Bridge sampling draws from R's random-number generator, so running the scripts, or the steps inside them, in a different order changes the marginal likelihood estimates slightly.

Everything is written to `output/`, which is created on the first run: `output/tables/` (CSV), `output/figures/` (PNG), `output/fits/` (cached Stan fits), `output/logs/` (`session_info.txt`).


## Repository structure
```
MSc-ERP-project/
├── README.md
├── R/
│   ├── 00_setup.R                             Packages, paths, data
│   ├── 01_data_validation_and_eda.R           Table 1, Table 2, Figures 1-6
│   ├── 02_RQ1_exposure_metric_comparison.R    Table 3, Tables A1-A3
│   └── 03_RQ2_RQ3_duration_household.R        Table 4, Table A4, Figures 7, 8, A1
├── stan/
│   └── bernoulli_logit_cauchy.stan            The Stan model used by all analyses
├── data/
│   └── bht_IndividualsData.csv                Participant-level dataset (49 participants)
└── output/                                    
```

