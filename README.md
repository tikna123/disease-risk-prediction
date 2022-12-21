# Disease Risk Prediction
# 1. Problem Definition
Given the profiles data about the patients and risk data that containts a measure of risk those individuals have with
respect to certain diseases. Perform Exploratory data anlaysis on the these datasets. Build a model to predict the risk of 
cancer from individual's profile features.

# 2. Exploratory data anlaysis
## 2.1 Dataset details
There are two files
* profiles.csv: It contains following features about the individual
    * ID: unique identifier for an individual
    * Sex: Male/Femal
    * Age: Age of the individual
    * Smoking: Smoking status.(yes/no)
    * BMI: Body Mass Index
    * Heart rate data used: whether the individual submitted heart rate data with steps information
* risks.csv: It contains following columns
    * ID: unique identifier for an individual
    * Disease: The disease of interest
    * Risk: A measure of the risk associated with the individual getting the
    disease. Only individuals with a risk greater than zero for a
    particular disease are included
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/2.1_1.PNG" width="500">
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/2.1_2.PNG" width="500">

## 2.2 Categorical variables
* Smoking status vs age
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/2.2_1.png" width="500">

* MET vs sex
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/2.2_2.png" width="500">

## 2.3 Detecting outliers with Numerical variables
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/2.2_3_age.png" width="500">
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/2.2_3_2.png" width="500">
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/2.2_3_met.png" width="500">
* Age variable looks fine
* For BMI, one value was close to 270 which is abnormal.
* Interquantile range method is used to identify outliers.
* For MET, there are lot of values>50.
* Remove all the rows for which MET>50
* Remove row with BMI value equals to 270
## 2.4 Cancer disease distribution
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/2.2_4.png" width="500">
## 2.5 Risk sum analysis
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/2.2_5_1.png" width="500">
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/2.2_5_2.png" width="500">

# 3. ML Models to estimate risk of cancer
* I tried following models
   * Linear regression with feature normalization
   * Random forest
   * Gradient Boosting
    * XGBoost
    * LightGBM
    * Catboost
* I have used RMSE as evaluation metrics to compare different models.
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/2.2_5_2.png" width="500">

# 4. Feature Importance
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/4.1.png" width="500">
<img src="https://github.com/tikna123/disease-risk-prediction/blob/main/images/4.2.png" width="500">
* By looking at the shap values we can conclude following
    * Non smoker person have a very low risk of getting cancer and vice versa.
    * IF MET value for a patient is high, then chance of getting cancer is low and vice versa.
    * Higher the Age, higher the chances of getting the cancer.
    * Higher the BMI, higher the chances of getting the cancer.
    * For this particular dataset, Male generally have a lower chance of getting cancer.
* Smoking status, BMI, MET, Age, Sex are the most significant feature to
calculate the risk score.