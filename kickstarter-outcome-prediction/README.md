# Kickstarter Campaign Prediction (2019)

Predicting campaign success/failure using 331,675 Kickstarter campaigns from 2009-2018. My first experience working with messy real-world data at scale.

## What I Built

Tried to predict whether a Kickstarter would succeed or fail based on:
- Goal amount (converted to USD)
- Category/subcategory (Film, Music, Games, etc.)
- Launch timing (day of week, hour, week of year)
- Campaign duration
- Geographic location
- Number of backers

## The Data Cleaning Journey

This dataset was rough. Multiple currency formats, inconsistent datetime fields, missing values scattered throughout. Spent most of my time in `data-cleaning.ipynb` just getting it into usable shape:

- Dropped campaigns with status "live", "canceled", "suspended" (kept only success/fail)
- Converted all currencies to USD using two different rate sources (reconciled conflicts)
- Extracted datetime features: day of week, week of year, hour of launch, campaign duration
- Combined duplicate columns (had both `usd pledged` and `usd_pledged_real`)

## Project Structure

Analysis split across multiple notebooks (this was before I learned to organize better):
- `choosing-data-set.ipynb` - Dataset evaluation
- `data-cleaning.ipynb` - **Most important one** - all the preprocessing
- `initial-data-exploration.ipynb` - Basic EDA
- `more-exploration.ipynb` - Deeper category/timing analysis
- `machine-learning-models.ipnyb` - Classification models (note: typo in filename)

## What I Learned

**Good:**
- Got comfortable with pandas datetime operations
- Learned to handle multiple currencies and coordinate system conversions
- Working with categorical data at scale

**What I'd Improve:**
- Notebooks are disorganized (should be 1-2 files max)
- No clear final model or results documented
- Didn't properly validate findings on holdout set
- Could have used campaign text/descriptions (NLP) but didn't
- No analysis of whether timing actually matters or just correlates with category

## Dataset Source

Kaggle: [Kickstarter Projects](https://www.kaggle.com/kemical/kickstarter-projects)

Note: Dataset not included. Download separately and update paths in notebooks.
