[![Gitpod Ready-to-Code](https://img.shields.io/badge/Gitpod-Ready--to--Code-blue?logo=gitpod)](https://gitpod.io/#https://github.com/Burton-David/datascience-projects)

# Data Science Bootcamp Work (2019)

This repository contains projects from Flatiron School's Data Science bootcamp, completed between January and October 2019. I'm keeping these public as a record of my learning journey and foundations in data science.

**Status:** These are archived learning projects. The code reflects techniques and libraries from 2019 and has not been updated to current standards. Notebooks may require dataset downloads and dependency adjustments to run.

## What's Here

### Credit Card Fraud Detection
Tackled the classic imbalanced classification problem using the Kaggle credit card fraud dataset. Compared 7 different algorithms on a balanced subsample. Best result: Linear Discriminant Analysis with 0.98 ROC-AUC on cross-validation.

**Key learning:** Dealing with severe class imbalance (99.8% legitimate transactions). Used random undersampling to create balanced training set, applied t-SNE for visualization.

### Kickstarter Campaign Prediction
Analyzed 300k+ Kickstarter campaigns to predict success/failure. Heavy focus on feature engineering from datetime fields and exploratory analysis of campaign categories and timing.

**Key learning:** Data cleaning on messy real-world data with multiple date formats, currency conversions, and missing values.

### Real Estate Price Prediction
Linear regression for housing price prediction. My first project working with continuous target variables and multiple regression.

**Key learning:** Foundation in regression diagnostics, residual analysis, and feature selection.

### Student Outcome Prediction
Classification project predicting student academic performance.

**Key learning:** Working with demographic data and understanding model interpretation for sensitive use cases.

## Tech Stack (2019)
Python 3.6-3.7, pandas, numpy, scikit-learn, matplotlib, seaborn, XGBoost, Jupyter notebooks

## Note on Running These
Datasets are not included in this repo due to size. Most came from Kaggle and would need to be downloaded separately. Code uses 2019-era library versions and syntax that may throw deprecation warnings with current versions.

## What I'd Do Differently Now
- Use proper experiment tracking (MLflow, Weights & Biases)
- Add cross-validation strategies beyond simple train/test splits
- Deploy at least one model as a demo API
- Use more modern tools like Poetry for dependency management
- Write unit tests for data processing functions
- Add proper logging instead of print statements