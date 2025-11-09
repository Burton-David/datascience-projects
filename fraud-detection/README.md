# Credit Card Fraud Detection (2019)

Comparing seven classification algorithms on heavily imbalanced credit card transaction data. This was one of my early projects learning to handle class imbalance.

## The Challenge

Dataset: 284,807 credit card transactions
- Fraudulent: 492 (0.17%)
- Legitimate: 284,315 (99.83%)

This extreme imbalance was the real challenge. Train on the full dataset and any model will just predict "legitimate" for everything and get 99.8% accuracy while being completely useless.

## What I Did

**Data Handling:**
- Scaled Time and Amount features using StandardScaler
- Created balanced training subsample: randomly selected 441 legitimate transactions to match 441 fraudulent ones
- Applied IQR method to remove extreme outliers (kept within 2.5 * IQR)
- Used t-SNE to visualize separation between classes in 2D

**Feature Analysis:**
- V4 and V11 showed strongest positive correlation with fraud (0.71, 0.68)
- V3, V9, V10, V12, V14, V16, V17 showed strong negative correlation (below -0.5)
- These features are PCA-transformed so can't interpret what they mean in business terms

**Models Tested (10-fold cross-validation, ROC-AUC scoring):**
1. Linear Discriminant Analysis: **0.9808** (winner)
2. Logistic Regression: 0.9781
3. SVM: 0.9746
4. XGBoost: 0.9738
5. Random Forest: 0.9734
6. K-Nearest Neighbors: 0.9618
7. Decision Tree: 0.8766

## What I Learned

**Good:**
- Random undersampling worked well for this problem
- LDA performed surprisingly well (simple but effective)
- Feature correlation analysis helped understand what drives fraud

**What I'd Change:**
- Should have tried SMOTE or other oversampling techniques, not just undersampling
- Didn't test the final model on the full imbalanced test set (rookie mistake)
- No precision-recall curves, only ROC-AUC (precision matters more for fraud detection)
- Balanced subsample threw away 99.9% of legitimate transactions - wasteful
- Should have used stratified k-fold explicitly
- No cost-sensitive learning approaches

## Dataset Source

Kaggle: [Credit Card Fraud Detection](https://www.kaggle.com/mlg-ulb/creditcardfraud)

Features V1-V28 are PCA transformations (privacy protection). Only Time, Amount, and Class (target) are interpretable.

Dataset path in notebook (`../datasets/creditcard.csv`) won't work without downloading it first.

## Files
- `fraud-detection.ipynb` - Full analysis notebook
- `tree.dot` - Decision tree visualization export
