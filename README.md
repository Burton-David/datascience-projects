[![Gitpod Ready-to-Code](https://img.shields.io/badge/Gitpod-Ready--to--Code-blue?logo=gitpod)](https://gitpod.io/#https://github.com/Burton-David/datascience-projects)

# Data Science Bootcamp Projects (2019)

This repository contains projects from Flatiron School's 10-month Data Science bootcamp, completed between January and October 2019. These represent my foundation in data science and machine learning fundamentals. I'm keeping them public as a record of my learning journey.

**Important Context:** These are archived learning projects from 2019. The code uses libraries and techniques from that era and has not been updated to current standards. Datasets are not included and would need to be downloaded separately. Notebooks may require dependency adjustments to run with modern library versions.

---

## Projects

### 1. Credit Card Fraud Detection
**Location:** `fraud-detection/`

**The Challenge:**
Detecting fraudulent transactions in a severely imbalanced dataset (284,807 transactions, only 0.17% fraudulent). This was one of my first projects dealing with class imbalance, where naive models would achieve 99.8% accuracy by simply predicting everything as legitimate.

**What I Did:**
- Scaled Time and Amount features using StandardScaler
- Created balanced training subsample by randomly undersampling legitimate transactions (441 fraud, 441 legitimate)
- Applied IQR method to remove extreme outliers (2.5 * IQR threshold)
- Performed correlation analysis to identify key features (V4, V11 positively correlated; V3, V9, V10, V12, V14, V16, V17 negatively correlated)
- Used t-SNE for 2D visualization of class separation
- Compared 7 classification algorithms using 10-fold cross-validation with ROC-AUC scoring

**Results:**
1. Linear Discriminant Analysis: 0.9808 ROC-AUC (best performer)
2. Logistic Regression: 0.9781
3. SVM: 0.9746
4. XGBoost: 0.9738
5. Random Forest: 0.9734
6. K-Nearest Neighbors: 0.9618
7. Decision Tree: 0.8766

**What I Learned:**
Random undersampling worked well but was wasteful (discarded 99.9% of legitimate transactions). LDA surprisingly outperformed ensemble methods on this balanced subsample. Should have tested models on the full imbalanced test set and used precision-recall curves instead of just ROC-AUC, since precision matters more for fraud detection in production.

**Dataset:** [Kaggle Credit Card Fraud Detection](https://www.kaggle.com/mlg-ulb/creditcardfraud)

---

### 2. Kickstarter Campaign Prediction
**Location:** `kickstarter-outcome-prediction/`

**The Challenge:**
Predicting whether Kickstarter campaigns would succeed or fail using 331,675 campaigns from 2009-2018. This was my first experience working with messy real-world data at scale.

**What I Did:**
- Extensive data cleaning: reconciled two different USD conversion sources, handled multiple currency formats
- Dropped campaigns with ambiguous status (live, canceled, suspended) to focus on clear success/failure
- Feature engineering from datetime fields: day of week, week of year, hour of launch, campaign duration
- Extracted features from goal amounts, categories, and geographic data
- Exploratory analysis of campaign timing and category relationships

**Project Structure:**
Analysis split across multiple notebooks (before I learned better organization):
- `choosing-data-set.ipynb` - Dataset evaluation
- `data-cleaning.ipynb` - Heavy preprocessing work
- `initial-data-exploration.ipynb` - Basic EDA
- `more-exploration.ipynb` - Category and timing analysis
- `machine-learning-models.ipnyb` - Classification models (note the typo in filename)

**What I Learned:**
Data cleaning took longer than modeling. Got comfortable with pandas datetime operations, currency conversions, and handling missing values. However, notebooks are disorganized, I didn't document clear final model results, and never properly validated on a holdout set. Could have incorporated NLP on campaign descriptions but didn't.

**Dataset:** [Kaggle Kickstarter Projects](https://www.kaggle.com/kemical/kickstarter-projects)

---

### 3. Real Estate Price Prediction
**Location:** `real-estate-analysis/predict-housing-price-using-linear-regression/`

**The Challenge:**
My first linear regression project. Classic housing price prediction to learn regression fundamentals.

**What I Did:**
- Checked linear regression assumptions (linearity, homoscedasticity, normality of residuals)
- Feature selection to handle multicollinearity
- Interpreted coefficients and p-values
- Residual analysis to validate model fit
- Basic train/test split evaluation

**What I Learned:**
This was about building foundation in regression diagnostics. Learned why R² isn't everything, how to interpret model coefficients, and the importance of checking assumptions. The notebook is basic by current standards but served its purpose as an introduction to regression.

**Honest Assessment:** This was a learning exercise. Would I put it on a resume? No. But it's part of the progression.

---

### 4. Student Outcome Prediction
**Location:** `student-outcome-prediction/`

**The Challenge:**
Predicting student academic performance using demographic and behavioral data. Classification project focused on identifying at-risk students.

**What I Did:**
- Applied classification techniques to predict academic outcomes
- Used features including demographics, attendance patterns, prior academic performance, socioeconomic indicators
- Focused on model accuracy and performance metrics

**What I Learned:**
This was my first project dealing with sensitive data where mistakes have real consequences. Made me think about fairness and bias in predictive models, the ethics of using demographic data, and what happens when you optimize for the wrong metric. Looking back, I focused too much on accuracy scores and not enough on:
- Feature importance (which factors actually drive outcomes?)
- Fairness metrics across demographic groups
- Whether predictions would actually help students or just label them
- What interventions could follow from predictions

This project made me realize data science isn't just about accuracy scores. Interpretability and ethical considerations matter more in some domains than raw performance.

---

## Technology Stack (2019)

**Original Environment:**
- Python 3.6-3.7
- pandas ~0.24
- numpy ~1.16
- scikit-learn ~0.21
- matplotlib ~3.0
- seaborn ~0.9
- xgboost ~0.90
- Jupyter notebooks

**Note on Dependencies:**
The notebooks use 2019-era syntax and may throw deprecation warnings with current library versions. `requirements.txt` includes approximate modern equivalents if you want to try running them, but they haven't been tested with current versions.

---

## How I'd Approach These Differently Today

With 5 years of experience since completing these projects, here's what I would change:

**Experiment Tracking & Reproducibility:**
- Use MLflow or Weights & Biases to track experiments systematically
- Implement proper config management (Hydra, OmegaConf)
- Use Poetry or conda for dependency management instead of basic requirements.txt
- Add random seeds everywhere for reproducibility

**Model Development:**
- Use stratified k-fold cross-validation explicitly (not just random splits)
- Implement proper train/validation/test splits with holdout sets
- For imbalanced data: try SMOTE, ADASYN, and cost-sensitive learning instead of just random undersampling
- Use precision-recall curves and F-beta scores for imbalanced problems, not just ROC-AUC
- Implement hyperparameter tuning with Optuna or Ray Tune

**Code Quality:**
- Write modular Python scripts instead of monolithic notebooks
- Add unit tests for data processing and feature engineering functions
- Use proper logging (loguru, structlog) instead of print statements
- Implement data validation with Great Expectations or Pandera
- Version control datasets with DVC

**Deployment & Production:**
- Deploy at least one model as a REST API (FastAPI)
- Containerize with Docker
- Add model monitoring and drift detection
- Create simple front-end demos for non-technical stakeholders

**Documentation:**
- Add data cards and model cards documenting assumptions, limitations, and intended use
- Include environment setup instructions that actually work
- Document data preprocessing steps in a reproducible pipeline
- Add visualizations and results directly in README files

**Ethics & Fairness:**
- For sensitive applications (student outcomes), conduct bias audits
- Use fairness metrics (demographic parity, equalized odds)
- Document potential harms and mitigation strategies
- Consider whether the model should even be built

---

## Repository Status

These projects are preserved as-is to show my learning foundation. They contain typical beginner mistakes (data leakage risks, poor organization, missing validation) that I've learned to avoid. For examples of more mature work with modern practices, see [link to current portfolio if you have one].

Datasets are not included due to size. All came from Kaggle and would need to be downloaded separately. File paths in notebooks will need adjustment.