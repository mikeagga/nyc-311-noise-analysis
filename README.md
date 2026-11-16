# NYC 311 Noise Complaint Closure Time Analysis

Exploratory data analysis, spatial feature engineering, and logistic regression modeling of NYPD 311 noise complaint closure times across New York City.

- **Report (PDF):** [nyc-311-noise-analysis.pdf](nyc-311-noise-analysis.pdf) (also available in [Releases](https://github.com/mikeagga/nyc-311-noise-analysis/releases))
- **Analysis Source:** [analysis.qmd](analysis.qmd)

## Overview

This project investigates the factors associated with NYPD 311 noise complaint closure times across New York City boroughs, focusing on complaints taking more than two hours to close (`over2h`).

### Key Steps

1. **Data Cleaning & Standardization**
   - Cleaned and standardized 14,000+ NYPD 311 noise complaint records.
   - Validated NYC ZIP codes, resolved redundant location/borough fields, verified timestamp consistency, and geocoded missing coordinates via the OpenCage API.
2. **Exploratory Data Analysis & Hypothesis Testing**
   - Analyzed closure times across time of day (day vs. night), day of week (weekday vs. weekend), complaint descriptors, and boroughs using t-tests, one-way ANOVA, and chi-square tests.
   - Identified significant borough-level differences in the proportion of complaints taking over two hours to close (e.g., 26.9% in the Bronx vs. 16.6% in Brooklyn).
3. **Spatial & Socioeconomic Feature Engineering**
   - Computed incident-to-nearest-precinct distances using scaled coordinates and a SciPy `cKDTree` spatial index.
   - Merged ZIP-code-level median household income from U.S. Census data.
4. **Predictive Modeling**
   - Trained and evaluated a class-balanced logistic regression model (`scikit-learn`) predicting `>2`-hour closure times on an 80/20 train/test split (ROC-AUC: `0.60`), examining feature coefficients and limitations of predicting dispatch/closure duration from static call attributes.

## Tools & Libraries

- **Python:** `pandas`, `NumPy`, `SciPy`, `scikit-learn`, `Matplotlib`, `Seaborn`, `PyArrow`, `opencage`
- **Quarto:** `analysis.qmd`
