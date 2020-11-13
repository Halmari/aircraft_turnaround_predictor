# Interpretable machine learning for prediction of aircraft turnaround durations

This repository contains the main points from my thesis where I present a model which predicts turnaround durations of an aircraft and also provides interpretability for the predictions. Predictions are made with a machine learning algorithm XGBoost and interpretability is provided with interpretability framework SHAP.

**Main technologies used in the process:**
- Pandas
- Scikit-learn
- XGBoost
- SHAP
- Seaborn & Matplotlib

The link for the thesis will be provided after it is available in the university library site.
<br/><br/>
<p align="center">
  <img src="/images/turnaround.jpg" alt="Finnair aircraft turnaround" width="600"/>
</p>
<p align="center">(Photo by Finnair)</p>

## Process

**The following process was performed in the analysis:**
- Data preprocessing
    - Joining of data tables
    - Removal of duplicates and null values
- Removal of outliers
- Inspection of interactions between variables and collinearity
    - H-statistic
    - SHAP
    - Correlation matrix
    - Variance inflation factor (VIF)
- Feature selection
    - Recursive feature elimination
- XGBoost model training and assessment
    - Cross-validation and hyperparameter tuning
    - Mean absolute error (MAE) and explained variance (R<sup>2</sup>) 


## Results

