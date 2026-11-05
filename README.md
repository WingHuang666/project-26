# project-26

# Global Academic Retractions Analysis (2000–2025)

## 1. Project Overview

This project analyzes global academic retraction records using exploratory data analysis (EDA), machine learning, and clustering techniques. The objective is to investigate publication characteristics, predict retraction-related outcomes, identify important features, and explore patterns among retracted academic papers.

The analysis is conducted in Python using multiple regression, classification, and unsupervised learning models.

## 2. Dataset Description

**Dataset:** Global Academic Retractions (2000–2025)

The dataset contains 65,909 records and 18 original variables, covering publication information, academic disciplines, authorship, countries, retraction dates, and retraction reasons.

Key variables include:

- **Publication Information:** `title`, `journal`, `publisher`, `article_type`
- **Academic Disciplines:** `primary_subject`, `subject_areas`
- **Geographic Information:** `primary_country`, `country`
- **Authorship:** `authors`, `author_count`
- **Dates:** `original_paper_date`, `retraction_date`, `days_to_retraction`
- **Retraction Information:** `retraction_reasons`, `is_misconduct`

The dataset includes original publication dates from 2000 to 2025 and retraction dates extending into 2026.

## 3. Research Questions

The project investigates five research questions:

**RQ1: Retraction Delay Prediction (Regression)**

Can publication characteristics predict the time between publication and retraction, and which features are most influential?

**RQ2: Misconduct Classification (Binary Classification)**

Can publication characteristics predict whether a retraction is classified as misconduct-related?

**RQ3: Data-Related Retraction Classification (Binary Classification)**

Can publication characteristics predict whether a retraction involves data-related issues?

**RQ4: Health-Related Subject Classification (Binary Classification)**

Can publication characteristics predict whether a retracted paper belongs to a health-related academic subject?

**RQ5: Retraction Pattern Clustering (Unsupervised Learning)**

Can retracted academic papers be grouped into distinct clusters based on publication characteristics?

## 4. Data Preprocessing

The project includes several preprocessing steps:

- Combining two CSV files into a single dataset.
- Checking missing values, duplicate records, and data consistency.
- Converting date variables and validating retraction durations.
- Processing multi-value text variables, including subject areas, countries, authors, and retraction reasons.
- Applying multi-hot encoding to appropriate categorical variables.
- Using TF-IDF to preserve information from article titles.
- Encoding categorical features and scaling numerical variables where appropriate.
- Creating additional features such as publication year, title word count, and numbers of subjects and countries.
- Excluding target-derived variables when necessary to prevent data leakage.

Missing DOI values are retained because these identifiers are not essential predictors for the main research questions.

## 5. Exploratory Data Analysis (EDA)

EDA is performed to understand the dataset's structure and characteristics before modeling.

The analysis includes:

- Data quality and missing-value assessment.
- Annual retraction trends.
- Distribution of retraction delays.
- Frequency of recorded retraction reasons.
- Distribution across academic disciplines.
- Examination of multi-value text variables.

Visualizations are generated using Matplotlib and Seaborn.

## 6. Machine Learning Models

The project compares multiple candidate models for each supervised learning task.

| Task | Models | Primary Evaluation |
|---|---|---|
| RQ1: Regression | Dummy Median, Ridge, Random Forest, Extra Trees | MAE |
| RQ2: Classification | Dummy Prior, Logistic Regression, Random Forest, Extra Trees | PR-AUC |
| RQ3: Classification | Dummy Prior, Logistic Regression, Random Forest, Extra Trees | PR-AUC |
| RQ4: Classification | Dummy Prior, Logistic Regression, Random Forest, Extra Trees | PR-AUC |

Additional evaluation metrics include:

- **Regression:** RMSE and R²
- **Classification:** ROC-AUC, F1 Score, and Balanced Accuracy

Models are compared using cross-validation, and the selected models are evaluated on independent holdout datasets.

Permutation Importance is used to identify influential input features. Model-specific visualizations are generated for non-dummy models.

## 7. Clustering Analysis

RQ5 applies K-means clustering to explore similarities among retracted publications.

The clustering workflow includes:

1. Preparing and transforming input features.
2. Evaluating candidate K values using the Elbow Method.
3. Calculating Silhouette Scores.
4. Selecting a suitable K based on both metrics and cluster interpretability.
5. Examining cluster sizes and characteristics.
6. Visualizing clusters using two-dimensional Truncated SVD projections.

Random seeds are used to improve reproducibility.

## 8. Tools and Libraries

**Programming Language:** Python

**Development Environment:** Jupyter Notebook / Quarto / GitHub Codespaces

**Main Libraries:**

- `pandas` — Data manipulation and preprocessing
- `numpy` — Numerical operations
- `matplotlib` — Data visualization
- `seaborn` — Statistical visualization
- `scikit-learn` — Machine learning, preprocessing, evaluation, and clustering
- `scipy` — Scientific computing and sparse matrix operations

## 9. Project Structure

```text
Global-Academic-Retractions/
│
├── global_retractions_research.qmd
├── global_academic_retractions_2000_2025_1.csv
├── global_academic_retractions_2000_2025_2.csv
└── README.md
```

The original dataset is divided into two CSV files for easier GitHub uploading. Both files are combined during data loading.
