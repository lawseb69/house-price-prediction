# House Price Prediction – Portfolio Project

End-to-end regression project to predict residential house sale prices using the Kaggle **House Prices: Advanced Regression Techniques** dataset.  
The goal is to build a robust model for `SalePrice` and understand which property characteristics drive higher or lower prices.

## Project overview

- **Problem**: Predict the final sale price of homes based on 80+ features describing location, size, quality, and other characteristics.  
- **Target**: `SalePrice` (USD).  
- **Tools**: Python, pandas, scikit-learn, matplotlib, seaborn, Kaggle Notebooks. 

## Data

- **Rows**: 1,460 houses (training set).  
- **Columns**: 80 features + `SalePrice`. 
- **Source**: Kaggle – House Prices: Advanced Regression Techniques.  
- Data files are not stored in this repository; download `train.csv` from Kaggle and place it under `data/` or attach it in Kaggle Notebooks. 

## Methodology

1. **Data cleaning**
   - Removed ID column (`Id`) and very sparse features with >80–90% missing values (`PoolQC`, `MiscFeature`, `Alley`, `Fence`).  
   - Handled remaining missing values through a preprocessing pipeline:
     - Numeric: median imputation.  
     - Categorical: most-frequent imputation. 

2. **Exploratory Data Analysis (EDA)**
   - Analyzed the distribution of `SalePrice` (right-skewed, with a few very expensive properties).  
   - Visualized relationships between price and key features such as living area (`GrLivArea`), overall quality (`OverallQual`), basement/garage size, and neighborhood. 

3. **Modeling**
   - Train/test split (80/20) to evaluate on unseen data. 
   - Built a scikit-learn `Pipeline` with `ColumnTransformer` for preprocessing plus:
     - **Linear Regression** (baseline).  
     - **GradientBoostingRegressor** (final model).

4. **Evaluation**
   - **Linear Regression**: RMSE ≈ **31,227** USD, R² ≈ **0.87**. 
   - **Gradient Boosting**: RMSE ≈ **26,992** USD, R² ≈ **0.91** → selected as the final model. 

## Key insights

- Higher **overall quality** (`OverallQual`) and larger **above-ground living area** (`GrLivArea`) are the strongest drivers of higher sale prices. 
- Houses with larger **basements** and greater **garage capacity** (e.g., `TotalBsmtSF`, `GarageCars`) tend to be more expensive.  
- **Newer or recently remodeled** houses generally sell for higher prices than older properties. [web:7]  
- **Neighborhood** features show that location has a major impact on price, with clear differences in median house prices between areas. 

## How to run

1. Install dependencies:

2. Download `train.csv` from Kaggle and place it under `data/`. 

3. Open the notebook:

4. Run all cells to reproduce the analysis and model results.

## Future work

- Perform more extensive hyperparameter tuning and cross-validation for Gradient Boosting and other tree-based models (e.g., XGBoost, LightGBM).
- Experiment with log-transformed prices and additional engineered features (price per square meter, age buckets).  
- Deploy the model as a simple web app to allow interactive house price estimation.
