# Mental-Health-Burnout-Prediction-Dataset

# Mental Health & Burnout Prediction

## Project Overview

This project focuses on predicting employee burnout risk using machine learning and deep learning techniques.

The dataset contains information related to work patterns, lifestyle, mental health indicators, and personal characteristics. The goal is to classify individuals into three burnout-risk categories:

- Low
- Moderate
- High

The project follows an end-to-end machine learning workflow, starting from exploratory data analysis and data preprocessing, followed by model development, evaluation, hyperparameter tuning, and neural network development.

---

## Dataset

The dataset contains:

- **50,000 observations**
- **40 variables**
- **35 predictor variables** used for modelling
- **3 target classes**

The target variable is:

`Burnout_Risk`

The three classes are:

- `Low`
- `Moderate`
- `High`

### Important Variables

Some of the variables used in the analysis include:

- Age
- Monthly Income
- Work Hours per Week
- Job Satisfaction
- Work-Life Balance
- Sleep Hours
- Anxiety Score
- Depression Score
- Mood Score
- Emotional Stability
- Physical Activity Hours
- Meditation Minutes
- Screen Time Hours
- Productivity Score
- Stress Level
- Chronic Stress
- Sleep Quality
- Life Satisfaction

---

## Project Objectives

The main objectives of this project were to:

1. Explore the factors associated with burnout risk.
2. Clean and preprocess the dataset.
3. Identify and handle potential target leakage.
4. Build and compare different machine learning models.
5. Tune the best-performing classical machine learning model.
6. Build a neural network for burnout-risk classification.
7. Compare the neural network with classical machine learning models.
8. Select the best-performing model based on test-set performance.

---

## Exploratory Data Analysis

Exploratory data analysis was performed to understand the structure and relationships within the dataset.

The analysis included:

- Missing-value analysis
- Target-class distribution
- Numerical feature analysis
- Categorical feature analysis
- Correlation analysis
- Relationship between features and burnout risk
- Target leakage investigation

One important finding was that `Burnout_Score` was strongly related to `Burnout_Risk`. The burnout-risk categories corresponded closely to different burnout-score ranges.

Because `Burnout_Score` effectively represented the target, it was excluded from the predictive features to prevent data leakage.

`Mental_Health_Status` was also excluded because it had an almost deterministic relationship with the target variable.

`AI_Wellness_Recommendation` was excluded because it represented a recommendation/output rather than an appropriate predictive feature.

---

## Data Preprocessing

The dataset was divided into training and testing sets using an **80/20 stratified split**.

- Training set: **40,000 observations**
- Test set: **10,000 observations**

The 35 predictor variables consisted of:

- **19 numerical features**
- **16 categorical features**

### Numerical Features

Missing numerical values were handled using **median imputation**, followed by feature standardization using `StandardScaler`.

### Categorical Features

Missing categorical values were replaced using the most frequent category.

Categorical variables were then transformed using **One-Hot Encoding**.

After preprocessing, the 35 original predictors were transformed into **106 model-ready features**.

---

## Machine Learning Models

Several classical machine learning algorithms were trained and compared:

- Logistic Regression
- Decision Tree
- Random Forest
- Gradient Boosting
- Tuned Gradient Boosting

The models were evaluated using:

- Accuracy
- Precision
- Recall
- Macro F1-score
- Confusion Matrix

---

## Model Performance

The tuned Gradient Boosting model achieved the best performance among the models tested.

| Model | Accuracy | Precision | Recall | Macro F1 |
|---|---:|---:|---:|---:|
| Tuned Gradient Boosting | **81.88%** | **80.77%** | **79.91%** | **80.22%** |
| Logistic Regression | 81.82% | 80.36% | 79.56% | 79.92% |
| Gradient Boosting | 81.62% | 80.23% | 79.56% | 79.84% |
| Random Forest | 81.59% | 80.59% | 79.27% | 79.77% |
| Decision Tree | 75.41% | 72.91% | 72.97% | 72.94% |

---

## Hyperparameter Tuning

Randomized Search with stratified cross-validation was used to improve the Gradient Boosting model.

The best configuration included:

```text
n_estimators = 200
learning_rate = 0.03
max_depth = 2
min_samples_split = 2
min_samples_leaf = 2
subsample = 1.0
