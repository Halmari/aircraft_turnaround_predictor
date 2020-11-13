# Interpretable machine learning for prediction of aircraft turnaround durations

This repository contains the main points from my thesis where I present a model which predicts turnaround durations of an aircraft and also provides interpretability for the predictions. Predictions are made with a machine learning algorithm XGBoost and interpretability is provided with interpretability framework SHAP. Aircraft turnaround consists of sequence of tasks which prepare the aircraft for another journey and the aim is to describe those subprocesses with explicit input parameters such as passenger count and the amount of cargo on board.

Final trained model is capable of explaining approximately 60% of the variance in turnaround durations and mean absolute error for predictions is 2.81 minutes at best. In addition to point estimates, SHAP provides local explanations for single turnaround predictions by giving contributions of different feature variables on the prediction. More details can be found below and in the thesis.  

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

The following process was performed in the analysis:
- Data preprocessing
    - Joining of data tables
    - Removal of duplicates and rows with null values
- Removal of outliers
- Inspection of interactions between variables and collinearity
    - H-statistic
    - SHAP
    - Correlation matrix
    - Variance inflation factor (VIF)
- Exploratory data analysis (bivariate visualizations)
- Feature selection
    - Recursive feature elimination
- XGBoost model training and assessment
    - Cross-validation and hyperparameter tuning
    - Mean absolute error (MAE) and explained variance (R<sup>2</sup>)
- Interpretation of results with SHAP
    - Local and global explanations


## Results

As mentioned, the MAE for the best model is 2.81 minutes and data is capable of explaining 60% of the variance in the target variable turnaround time. Such level of performance combined with the capability of the model to explain contributions of different factors on the final prediction means that the model is successful as a proof-of-concept model in predicting turnaround times. It lays the foundation for further development and data collection in this kind of approach. Discovery and collection of data for additional varibles would improve the accuracies. Below are visualized some of the important results of the analysis. Units of some visualizations are removed to prevent distribution of confidential information.

### Performance metrics and distributions of residuals for different models 

In the figure and table below, distributions of residuals for different models are presented. Four models are provided with different subsets of feature variables which leads to different prediction accuracies. Individual models have also unique hyperparameters.
<br/><br/>

<p align="center">
  <img src="/images/residuals.png" alt="Residuals for different models" width="700"/>
</p>
<p align="center">Distributions of residuals for different XGBoost models</p>
<br/><br/>

<p align="center">
  <img src="/images/performance_table.png" alt="Performance table for different models" width="700"/>
</p>
<p align="center">Metrics for different XGBoost models</p>

### Global and local explanations provided by SHAP

Below are few selected visualizations to show the global and local effects of different variables. The SHAP Python framework is provided by [Scott Lundberg](https://github.com/slundberg/shap). SHAP summary plot demonstrates the effects of different feature variables on a global level. Color coding on the right side of the plot represents the value of a single observation for a specific feature. 
<br/><br/>

<p align="center">
  <img src="/images/shap_summary.png" alt="" width="600"/>
</p>
<p align="center">SHAP summary plot showing the global effects of different features</p>
<br/><br/>

SHAP dependency plot below shows the more detailed effect of a feature variable, in this case the number of departing passengers, on the predictions. In addition, another feature, the Deice variable, has been included in the plot as it demonstrates interaction effects with the number of departing passengers. Colored line on the right visualizes the values of the Deice variable.

<p align="center">
  <img src="/images/shap_36.png" alt="" width="500"/>
</p>
<p align="center">Metrics for different XGBoost models</p>
<br/><br/>

Lastly, waterfall plot below demonstrates the local explainability which means the contributions of different features on a single turnaround prediction. Waterfall plot starts from the expected turnaround duration and concludes on the final prediction by adding contributions of different features to the expected value. Values on the left are the feature values in this specific turnaround. 

<p align="center">
  <img src="/images/waterfall_best1.png" alt="" width="600"/>
</p>
<p align="center">Metrics for different XGBoost models</p>

