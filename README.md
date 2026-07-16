## Notebook
https://github.com/vipphan/practical-application-2/blob/main/prompt_II.ipynb

## Tools & Libraries used
Python
Pandas
Matplotlib
Seaborn
Scikit-learn

## Overview

This project analyzes a dataset of 426,880 used car listings (sourced from Craigslist via Kaggle) to identify the key factors that drive used car prices. The goal is to give a used car dealership clear, actionable insight into what consumers value, so they can make smarter inventory decisions — not just to build the most accurate predictive model possible.

The analysis follows the CRISP-DM framework: Business Understanding → Data Understanding → Data Preparation → Modeling → Evaluation → Deployment.

## Approach
### Data cleaning:
Filtered unrealistic price (kept $500–$200,000) and odometer (≤350,000 miles) values, handled missing data column-by-column (fill vs. drop depending on missingness rate), removed ~42K exact duplicate rows, and dropped high-cardinality columns (region, model, VIN, id, size).
### EDA:
Visualized price distributions and relationships with continuous variables (year, odometer) and key categorical variables (type, fuel, condition).
### Modeling:
Built and compared three regression models:

Baseline Linear Regression

Lasso Regression (tuned via GridSearchCV)

Linear Regression on a reduced feature set chosen via SequentialFeatureSelector (15 features)
### Evaluation:
Compared models using MAE and RMSE, and prioritized interpretability over raw predictive accuracy given the business goal.

## Key Findings
Vehicle type is one of the strongest price drivers — pickups and trucks sell for roughly $5,000 more than a comparable SUV.

Fuel type matters — diesel-powered vehicles price notably higher than gas, hybrid, or other fuel types.

Drivetrain and engine size — four-wheel drive and larger (8-cylinder) engines are associated with higher prices.

Age and mileage remain reliable value drivers, with a clear, consistent relationship to price.

Condition, surprisingly, did not show a clean or trustworthy pricing pattern in this dataset.

## Next Steps
Investigate condition_unknown: Listings missing a reported condition priced higher than expected, which doesn't have an obvious explanation yet and is worth digging into further.

Recover model-level signal: model was dropped due to high cardinality (20K+ unique values). Grouping rare models into an "other" bucket instead of dropping the column entirely could recover useful signal without blowing up the feature space.
