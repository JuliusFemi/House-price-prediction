# House Price prediction using regularized Linear Models

## Overview

This project aims to predict house sale prices using Linear Regression and regularized models such as Ridge and Lasso).
The target variable `SalePrice`, was log transformed to reduce skewness and normalize the distribution of the variable. After data cleaning, feature engineering and modeling, the best performing model was Ridge regression, with RMSE and R2 as the mterics. 


## Project Structure

- `predicting_house_prices.ipynb`: Jupyter Notebook containing full data preprocessing, model training, evaluation, and prediction steps.
- `datasset`: a folder housing the test and train data as well as saved data during analysis and modeling.
- `test_prediction.csv`: Final submission file containing predicted house prices on the test set (submitted to kaggle).
- `graphs/`: Folder containing plots for feature importance (Lasso and Ridge coefficients).
- `ProjectREADME.md`: This file.


## Data

The project uses the housing dataset provided in the challenge. It includes numerical and categorical variables describing physical attributes of homes (e.g., area, quality, zoning).
 Review the [data description](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt) for the data.


### Target Variable:
- `SalePrice`: Log-transformed for training (`Log_SalePrice`).
- 
### Features Used:
- Log-transformed skewed numeric features (e.g., `Gr Liv Area`, `Lot Area`)
- Ordinal-encoded quality variables (e.g., `Overall Qual`, `Kitchen Qual`)
- One-hot encoded categorical features (e.g., `Neighborhood`, `House Style`)


## Preprocessing

1. **Log Transformation** of highly skewed numerical features
2. **Ordinal Encoding** for ordered categorical variables
3. **One-Hot Encoding** for nominal categorical features
4. **Scaling** using `StandardScaler` after feature engineering
5. **Missing Value Handling**

## Models Tested

| Model             | RMSE  | R²    |
| ----------------- | ----- | ----- |
| Linear Regression | 0.141 | 0.873 |
| Ridge Regression  | 0.140 | 0.874 |
| Lasso Regression  | 0.141 | 0.872 |


**Best Model: Ridge Regression** with alpha=100



## Model Evaluation
- **Train/Test Split**: 80/20
- **Metrics**:
  - RMSE: 0.140 (on log scale)
  - R²: 0.874
- **Log Scale Error Interpretation**:  
  `exp(RMSE) ≈ exp(0.140) = 1.150`

## Feature Importance

- **Ridge Coefficients** (Top Predictors):
  - `Gr Liv Area` (living area)
  - `Overall Qual` (overall material quality)
  - `Lot Area`, `Garage Area`, `Exter Qual`, `Neighborhood_NridgHt`, etc.

- **Lasso Coefficients** were also visualized for each selected feature, this is to aid in understanding the effect of each feature on the Traget Variabke..

---

## Prediction and Submission

- The final Ridge model was used to predict the test dataset.
- The predictions were transformed back from log-scale using `np.expm1`.
- The submission file `test_prediction.csv` includes `Id` and `SalePrice`.

---

## Public Score on Kaggle

-  **Public Score**: `26530.26387`  
This score was achieved using the Ridge model with full preprocessing and log-transformed target.

---

## How to Run

1. Open `ridge_regression_house_prices.ipynb` in Jupyter Notebook
2. Run all cells in order
3. The final prediction CSV will be saved as `test_prediction.csv`

---

## Acknowledgments

- Data provided by Kaggle Housing Prices Advanced Regression Techniques competition.
- Model implementation using scikit-learn.


##  Refrence:

https://www.researchgate.net/publication/23534659_Determinants_of_House_Prices_A_Quantile_Regression_Approach
https://www.researchgate.net/publication/387822273_The_Research_on_Influencing_Factors_of_Housing_Price
https://www.youtube.com/watch?v=gMoJIH0prL4&list=PLeo1K3hjS3uu7clOTtwsp94PcHbzqpAdg&index=3
https://www.youtube.com/watch?v=cjBGLzOdX_0&list=PLfP3JxW-T70GM0TzYaDz4LtnADjXv1jFK

