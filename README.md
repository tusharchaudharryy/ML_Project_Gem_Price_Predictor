# 💎 Gemstone Price Prediction - Tushar Chaudhary

## 📊 Introduction About the Data

This project focuses on predicting the **price** of a diamond using regression analysis based on various physical and quality attributes.

### Dataset Description

There are 10 input features:

- `id` : Unique identifier of each diamond  
- `carat` : Weight of the diamond (in carats)  
- `cut` : Quality of the diamond cut  
- `color` : Diamond color grade  
- `clarity` : Purity and rarity of the diamond  
- `depth` : Height of the diamond from culet to table (in mm)  
- `table` : Width of the top facet relative to the widest point  
- `x` : Length of the diamond (in mm)  
- `y` : Width of the diamond (in mm)  
- `z` : Depth of the diamond (in mm)  

**Target Variable**:  
- `price` : The price of the diamond

📌 **Note**: The variables `cut`, `color`, and `clarity` are **ordinal categorical variables**.

### Reference for Grading Standards:
Refer to the [American Gem Society Grading System](https://www.americangemsociety.org/ags-diamond-grading-system/) for detailed classification of cut, color, and clarity.

---

## 🚀 Project Deployment

### Local Flask App

This project includes a web application built using **Flask** that allows users to input diamond features and get a predicted price.

### API Endpoint

An API endpoint is also available to accept POST requests and return price predictions in JSON format.

---

## 🔧 Project Structure and Workflow

### 1. Data Ingestion

- Load the dataset (`train.csv`)
- Split into training and test sets
- Save the processed datasets to `artifacts/`

### 2. Data Transformation

- Created a `ColumnTransformer` pipeline:
  - **Numerical features**: `SimpleImputer` (median) + `StandardScaler`
  - **Categorical features**: `SimpleImputer` (most frequent) + `OrdinalEncoder` + `StandardScaler`
- The preprocessor object is saved as a `.pkl` file

### 3. Model Training

- Evaluated several base models
- **Best performing model**: `CatBoostRegressor`
- Hyperparameter tuning applied to:
  - `CatBoost`
  - `KNN`
- Final model: `VotingRegressor` combining `CatBoost`, `XGBoost`, and `KNN`
- Saved trained model as a `.pkl` file

### 4. Prediction Pipeline

- Converts user inputs into a dataframe
- Loads preprocessing and model `.pkl` files
- Returns final prediction

### 5. Flask Web App

- User-friendly UI to collect inputs and display predicted gemstone price
- HTML + CSS integrated with Flask backend

---

## 📈 Notebooks

- **Exploratory Data Analysis (EDA)** – `1_EDA_Gemstone_price.ipynb`
- **Model Training & Selection** – `2_Model_Training_Gemstone.ipynb`
- **Model Explainability with LIME** – `3_Explainability_with_LIME.ipynb`

---

## 📦 Requirements

Install all required Python libraries:

```bash
pip install -r requirements.txt
