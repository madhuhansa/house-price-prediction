## 🏠 Project Overview: House Price Prediction

### 📊 Dataset Description

This project is based on a supervised machine learning regression task where the goal is to predict house sale prices using various features related to residential properties.

The dataset consists of two main files:

- `train.csv`: Contains 1460 rows and 81 columns. Each row represents a house with features like number of rooms, year built, lot size, location, and more — including the target variable `SalePrice`.
- `test.csv`: Contains similar data but without the `SalePrice` column. Your task is to predict this value.

The cleaned versions (`train_cleaned.csv` and `test_cleaned.csv`) are created after handling missing values, encoding categorical variables, and applying other preprocessing steps.

---

### 🎯 Problem Statement

The objective is to build a robust machine learning model that can:
- Accurately predict the house prices (`SalePrice`) for unseen data in the `test_cleaned.csv`.
- Handle a wide variety of feature types (categorical, numerical, ordinal).
- Optimize for metrics like R² Score, MAE (Mean Absolute Error), and RMSE (Root Mean Squared Error).

The final predictions are saved in `submission.csv` for evaluation or deployment purposes.

--- 

### ⛳skills
 
This project helps demonstrate skills in:
- handle large dataset (over 200 columns)
- Data preprocessing and cleaning 
- Feature selection and importance
- Regression model building (XGBoost, Gradient Boosting)
- Model tuning (GridSearchCV, Cross-validation)
- Practical use of scikit-learn and XGBoost for real-world data
  
---

## 📁 Project Structure

```
📦House Price Prediction
 ┣ 📂csv_files
 ┃ ┣ 📜submission.csv
 ┃ ┣ 📜test.csv
 ┃ ┣ 📜test_cleaned.csv
 ┃ ┣ 📜train.csv
 ┃ ┗ 📜train_cleaned.csv
 ┣ 📂model_pkl
 ┃ ┣ 📜best_gbr.pkl
 ┃ ┗ 📜best_model.pkl
 ┣ 📜model_train.ipynb
 ┣ 📜Predict.ipynb
 ┣ 📜test_cleaning.ipynb
 ┗ 📜train_cleaning.ipynb
📄 README.md (this file)
```
## 📄 Notebook File Descriptions


| File Name            | Description                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| model_train.ipynb    | Trains different machine learning models (e.g., XGBoost, Gradient Boosting) on the cleaned training dataset and evaluates performance. |
| Predict.ipynb        | Loads the best trained model and uses it to predict house prices on the cleaned test dataset. |
| test_cleaning.ipynb  | Cleans and preprocesses the raw test.csv data (e.g., handling missing values, encoding). |
| train_cleaning.ipynb | Cleans and preprocesses the raw train.csv data, preparing it for model training.        |

## 📘 Project Notebook Descriptions and Workflow

### 1. `train_cleaning.ipynb`
- 📂 Start by cleaning the `train.csv` dataset.
- 🧹 Handle a large number of missing values by:
  - Dropping irrelevant or sparse columns.
  - Creating new meaningful columns.
  - Using **regression imputation** to fill the `LotFrontage` column.
  - Filling with `"NO"` where the absence indicates "no feature present" (e.g., No Garage).
- 📉 Handle outliers by:
  - Visualizing distributions.
  - Understanding their impact.
  - Removing them manually.
- 📊 Exploratory Data Analysis (EDA):
  - Analyze how features relate to the sale price:
    - Bathroom-wise
    - Porch area-wise
    - Total Square Footage (TotalSF)
    - House Age
- 🛠 Feature Engineering:
  - Create new features like:
    - `TotalBathrooms`
    - `TotalPorchSF`
    - `TotalSF`
    - `NumFloors`
    - `HasPool`
    - `Age`, `SinceRemodel`, `IsRemodeled`, `IsNew`
- ✂ Drop unused or redundant features:
  - Apply label encoding where needed.
  - Drop features based on:
    - Low correlation with `SalePrice` (`< 0.1`)
    - High similarity (multi-collinearity)
- 💾 Save the cleaned dataset as `train_cleaned.csv`.

---

### 2. `test_cleaning.ipynb`
- 🔁 Apply the **same cleaning and transformation steps** to the `test.csv` dataset.
- 💾 Save the cleaned dataset as `test_cleaned.csv`.

---

### 3. `model_train.ipynb`
- 📥 Load `train_cleaned.csv`.
- 🧪 Train machine learning models:
  - **XGBoost Regressor** with hyperparameter tuning via Grid Search:
    - Best R² Score: `0.9166`
  - **Gradient Boosting Regressor** with Grid Search:
    - Best R² Score: `0.9155`
- 💾 Save the best models as:
  - `best_model.pkl` (XGBoost)
  - `best_gbr.pkl` (Gradient Boosting)

---

### 4. `Predict.ipynb`
- 📥 Load `test_cleaned.csv`.
- 📦 Load `best_gbr.pkl` model.
- 🔮 Predict `SalePrice` for test data.
- 📤 Save the predictions in `submission.csv`.

## 👤 Author
- yahan madhuhansa

