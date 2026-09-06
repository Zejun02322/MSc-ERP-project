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
R 4.5.1. Packages: rstan, bridgesampling, loo, bayesplot, tidyverse.
Data file `bht_IndividualsData.csv` is not included (see report, Section 3.1).

## How to run
Set `project_dir` at the top of each script, then run in order.

## Repository structure

| Script | Produces |
|---|---|
| 01_EDA.R | Table 1, Table 2, Figures 1–6 |
| 02_RQ1_model_comparison.R | Table 3, Appendix Tables A1, A2, A3 |
| 03_RQ2_RQ3_models.R | Table 4, Figure 7, Appendix Figures A1–A2, Appendix Table A4 |
Scripts 02 and 03 cache fitted models as .rds files
