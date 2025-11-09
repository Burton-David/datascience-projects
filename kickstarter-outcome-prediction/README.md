# Kickstarter Campaign Outcome Prediction

Predicting the success or failure of Kickstarter campaigns using historical project data.

## Overview
This project analyzes over 300,000 Kickstarter campaigns to predict whether a campaign will succeed or fail based on various features including category, goal amount, launch timing, and campaign duration.

## Dataset
Kickstarter Projects dataset from Kaggle containing campaign data from 2009-2018.

Source: https://www.kaggle.com/kemical/kickstarter-projects

## Project Structure
The analysis is broken into multiple notebooks:

- `choosing-data-set.ipynb` - Initial dataset selection and evaluation
- `data-cleaning.ipynb` - Data preprocessing, feature engineering, and handling missing values
- `initial-data-exploration.ipynb` - Exploratory data analysis
- `more-exploration.ipynb` - Additional feature analysis
- `machine-learning-models.ipnyb` - Model training and evaluation

## Key Features
- Campaign goal and pledged amounts (USD)
- Project category and subcategory
- Campaign duration
- Launch timing (day of week, hour, week of year)
- Geographic location

## Approach
1. Data cleaning and preprocessing
2. Feature engineering from datetime fields
3. Exploratory data analysis to identify patterns
4. Classification modeling to predict campaign outcomes

## Requirements
See root requirements.txt for dependencies.
