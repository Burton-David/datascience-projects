# Credit Card Fraud Detection

Binary classification analysis to detect fraudulent credit card transactions using machine learning.

## Overview
This project analyzes a highly imbalanced dataset of credit card transactions to identify fraudulent activity. The analysis includes extensive exploratory data analysis, feature correlation analysis, and comparison of multiple classification algorithms.

## Dataset
Uses the Credit Card Fraud Detection dataset from Kaggle. The dataset contains transactions made by European cardholders in September 2013. Features V1-V28 are PCA transformations of the original features for privacy reasons.

Note: The dataset is not included in this repository. Download from [Kaggle Credit Card Fraud Detection](https://www.kaggle.com/mlg-ulb/creditcardfraud).

## Approach
1. Exploratory data analysis and visualization
2. Feature scaling for Time and Amount columns
3. Creation of balanced subsample for training
4. Correlation analysis to identify key features
5. Outlier removal using IQR method
6. Dimensionality reduction with t-SNE
7. Model comparison across 7 algorithms

## Models Evaluated
- Logistic Regression
- Linear Discriminant Analysis
- K-Nearest Neighbors
- Decision Tree
- Support Vector Machine
- XGBoost
- Random Forest

## Results
Linear Discriminant Analysis achieved the highest ROC-AUC score of 0.98 on cross-validation.

## Requirements
See root requirements.txt file for dependencies.
