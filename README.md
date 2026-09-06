# U.S. Election & Census Machine Learning Analysis
## Project Overview

This project investigates how county-level demographic and socioeconomic characteristics are associated with voting outcomes in the 2024 U.S. presidential election.

I integrated U.S. county-level election results with Census demographic data, engineered socioeconomic features, and applied statistical learning and machine learning methods to classify county-level election outcomes.

The analysis combines exploratory data analysis, dimensionality reduction, clustering, feature selection, and supervised learning, with models evaluated using out-of-sample test data.

---

## Research Questions

This project focuses on three questions:

1. Which demographic and socioeconomic characteristics are most strongly associated with county-level voting outcomes?
2. How accurately can election winners be classified using Census characteristics?
3. Does dimensionality reduction improve predictive performance, or does it remove useful information?

---

## Data

Two county-level datasets were used:

- **Election Data:** 3,160 observations and 5 variables containing county-level election results.
- **Census Data:** 3,222 observations and 14 demographic and socioeconomic variables.

The datasets were cleaned and integrated using state and county identifiers.

Engineered features included:

- Median Household Income
- Male Population Percentage
- Female Population Percentage
- White Population Percentage
- Black Population Percentage
- Hispanic Population Percentage
- Urban / Rural Indicator

The classification target represents the winning political party in each county.

---

## Exploratory Data Analysis

Exploratory analysis was used to identify geographic, demographic, and socioeconomic patterns associated with election outcomes.

The analysis included:

- County and state-level election visualizations
- Comparison of household income distributions across election outcomes
- Demographic feature distributions
- Correlation analysis among Census predictors

These analyses provided context for subsequent dimensionality reduction and predictive modeling.

---

## Principal Component Analysis

Principal Component Analysis (PCA) was applied after centering and scaling the demographic predictors.

The first principal component was driven primarily by:

- Male population percentage
- Female population percentage
- White population percentage

Approximately **90% of the total variance** in the Census predictors required four principal components.

PCA was also evaluated as a reduced feature representation for clustering and classification.

---

## Hierarchical Clustering

Hierarchical clustering with complete linkage was used to identify groups of counties with similar demographic characteristics.

Two approaches were compared:

- Clustering using the original demographic predictors
- Clustering using PCA-transformed features

The PCA representation reduced redundancy among correlated variables and provided an alternative view of demographic similarity across counties.

---

## Classification Models

The merged dataset was divided using an **80/20 train-test split**, with cross-validation used for model selection and tuning where appropriate.

The following models were evaluated:

- Decision Tree
- Logistic Regression
- LASSO Logistic Regression
- Random Forest
- Gradient Boosting
- PCA-based Logistic Regression

---

## Model Performance

| Model | Test Error |
|---|---:|
| **Gradient Boosting** | **10.93%** |
| Logistic Regression | 11.09% |
| LASSO Logistic Regression | 11.09% |
| Random Forest | 11.09% |
| Decision Tree | 11.90% |
| PCA Logistic Regression | 14.47% |

**Gradient Boosting achieved the lowest test error at approximately 10.9%.**

Logistic Regression, LASSO, and Random Forest achieved similar out-of-sample performance, while the individual Decision Tree produced a slightly higher test error.

The PCA-based classifier produced a **14.47% test error**, indicating that reducing the predictors to only two principal components removed information useful for election classification.

---

## Key Findings

Several demographic and socioeconomic variables emerged as important predictors of county-level election outcomes.

Important features included:

- White population percentage
- Median household income
- Urban / rural status
- Hispanic population percentage
- Male population percentage

The Decision Tree selected **White population percentage** as its first split, while Logistic Regression identified several demographic and socioeconomic variables as statistically significant predictors.

Overall, the results demonstrate that Census characteristics contain substantial predictive information about county-level election outcomes.

These relationships should be interpreted as **associations rather than causal effects**.

---

## Model Comparison

The project illustrates the tradeoff between predictive performance and model interpretability.

### Decision Tree
- Highly interpretable
- Provides intuitive demographic decision rules
- Slightly weaker predictive performance

### Logistic Regression & LASSO
- Strong predictive performance
- Coefficients provide interpretable relationships
- LASSO enables feature selection through regularization

### Random Forest & Gradient Boosting
- Capture more complex relationships between predictors
- Provide strong out-of-sample performance
- Gradient Boosting achieved the lowest overall test error

### PCA-based Classification
- Reduces dimensionality and correlated information
- Simplifies the feature space
- Produced weaker predictive performance in this analysis

---

## Limitations

The models rely primarily on Census demographic and socioeconomic characteristics.

Voting behavior may also depend on factors not represented in these datasets, including political history, education, campaign activity, candidate characteristics, and local political conditions.

The results therefore demonstrate predictive associations rather than causal explanations of voting behavior.

---

## Technologies

- R
- tidyverse
- dplyr
- ggplot2
- PCA
- Hierarchical Clustering
- Logistic Regression
- LASSO
- Decision Trees
- Random Forest
- Gradient Boosting
- Cross-Validation
- ROC Analysis

---

## Repository Structure

```text
election-census-machine-learning/
│
├── README.md
└── election_census_analysis.Rmd
```

---

## Summary

This project demonstrates an end-to-end statistical learning workflow, from data integration and feature engineering to dimensionality reduction, model development, validation, and interpretation.

Among the evaluated methods, **Gradient Boosting achieved the best predictive performance with a 10.93% test error**, while simpler models such as Logistic Regression and LASSO provided comparable performance with greater interpretability.
