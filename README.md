# Default Payment Prediction

## Project Overview

This project develops a machine learning system to predict whether a credit-card customer will default on their next payment.

The project focuses on **feature selection, model benchmarking, and model evaluation using ROC-AUC**.

## Dataset

The dataset contains information about credit-card customers and their payment history.

* **Records:** 30,000
* **Original modeling features:** 23
* **Target:** `default payment next month`
* **Training/Test split:** 70% / 30%
* **Split type:** Stratified
* **Random state:** 42

The `ID` column was removed before modeling.

## Project Workflow

### 1. Data Preprocessing

The dataset was loaded and inspected using Pandas.

The following steps were performed:

* Checked the dataset shape and columns
* Checked data types
* Checked missing values
* Removed the `ID` column
* Separated features and target
* Created a stratified 70/30 train-test split

### 2. Feature Selection

Three feature-selection techniques were used.

#### Correlation Filter

Highly correlated features were identified using Pearson correlation.

A threshold of **0.80** was used to reduce redundant features.

This reduced the feature set from **23 to 16 features**.

#### Information Value (IV)

Information Value was calculated using the training data.

Features with **IV ≤ 0** were removed according to the project methodology.

The feature count remained at **16**.

#### SHAP Feature Selection

A LightGBM model was used to calculate SHAP feature importance.

The top **15 features** were selected for the final model benchmarking.

Final selected features:

* `PAY_0`
* `LIMIT_BAL`
* `BILL_AMT1`
* `PAY_AMT3`
* `PAY_AMT1`
* `PAY_5`
* `PAY_3`
* `PAY_AMT2`
* `PAY_2`
* `PAY_AMT6`
* `PAY_AMT5`
* `MARRIAGE`
* `PAY_AMT4`
* `AGE`
* `EDUCATION`

## Model Benchmarking

Six machine learning algorithms were compared:

* Logistic Regression
* LightGBM
* CatBoost
* XGBoost
* AdaBoost
* Random Forest

Hyperparameter tuning was performed using **GridSearchCV with 5-fold cross-validation**.

The optimization metric was **ROC-AUC**.

## Model Results

| Model               |   Test AUC | Precision | Recall | F1 Score |
| ------------------- | ---------: | --------: | -----: | -------: |
| CatBoost            |     0.7801 |    0.6590 | 0.3611 |   0.4666 |
| LightGBM            |     0.7767 |    0.6651 | 0.3581 |   0.4656 |
| XGBoost             |     0.7764 |    0.6601 | 0.3521 |   0.4592 |
| Random Forest       |     0.7743 |    0.6629 | 0.3526 |   0.4603 |
| AdaBoost            |     0.7618 |    0.6820 | 0.3134 |   0.4295 |
| Logistic Regression |     0.7124 |    0.6933 | 0.2441 |   0.3611 |

## Feature Selection Comparison

| Feature Selection Stage | Number of Features | Train AUC | Test AUC |
| ----------------------- | -----------------: | --------: | -------: |
| Original Features       |                 23 |    0.8895 |   0.7766 |
| Correlation Filter      |                 16 |    0.8832 |   0.7740 |
| IV Filter               |                 16 |    0.8832 |   0.7740 |
| SHAP Selection          |                 15 |    0.8817 |   0.7746 |

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* LightGBM
* CatBoost
* XGBoost
* SHAP
* SciPy
* Matplotlib
* Seaborn
* Joblib
* Jupyter Notebook

## Project Structure

```text
Default-Payment-Prediction/
│
├── default_payment_prediction.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## How to Run

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd Default-Payment-Prediction
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Add the dataset

Place the dataset file:

```text
default of credit card clients - Data.csv
```

in the project directory.

The dataset is not included in the GitHub repository.

### 4. Run the notebook

Open:

```text
default_payment_prediction.ipynb
```

using Jupyter Notebook or JupyterLab and run the cells from top to bottom.

## Skills Demonstrated

This project demonstrates practical experience with:

* Data preprocessing
* Stratified train-test splitting
* Feature selection
* Correlation analysis
* Information Value
* SHAP explainability
* Gradient boosting
* Hyperparameter tuning
* Cross-validation
* Model benchmarking
* ROC-AUC evaluation
* Classification metrics

## Disclaimer

This is an educational machine learning project. The model is not intended to make automated real-world financial decisions.
