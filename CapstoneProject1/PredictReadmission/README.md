## Hospital Readmission Prediction Rates for Diabetes patients 

Diabetes mellitus or diabetes as it is commonly known as, is a chronic, metabolic disease characterized by elevated levels of blood glucose (or blood sugar).
It is estimated that 9.3% of the population in the United States have diabetes, 28% of which are undiagnosed. The high prevalence of diabetes makes it a common comorbid condition in hospitalized patients. In recent years, government agencies and healthcare systems have increasingly focused on 30-day readmission rates to determine the complexity of their patient populations and to improve quality.

### Why we need to focus on 30-day Readmissions?
- Hospital readmission is a high-priority health care quality measure and target for cost reduction.
- The cost for hospital readmissions within 30 days of discharge is estimated to be close to $25 billion per year in the U.S. Patients with diabetes are frequently admitted to the hospital.
- Medicare(Insurance) counts the readmission of patients who returned to a hospital within 30 days and penalizes the hospital.

For these reasons, reducing the rate of hospital readmissions has great potential to help constrain health care costs and improve the quality of health care.

###  The problem - Is to predict if a diabetes patient will be readmitted within 30 days after the patient was discharged from the hospital, based on the patient's medical history information. 
 
## Dataset

The dataset is chosen from UCI Machine learning Repository - Diabetes 130-US hospitals for years 1999-2008 Data Set.
https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008

The dataset represents 10 years (1999-2008) of clinical care at 130 US hospitals and integrated delivery networks. . 
The dataset has 101766 observations and 50 attributes representing patient related medical history.

### Target variable 
Since the goal of our model will be to predict whether a patient will get readmitted to the hospital.
The readmitted attribute has the following values
 - '<30' - if the patient was readmitted in less than 30 days
 - '>30' - if the patient was readmitted in more than 30 days
 - 'No'  - if the patient was not readmitted

 The problem wil be tackled as a multiclass classification problem

## Data Wrangling
The dataset from UCI had considerable data that needed to be cleaned. Missing values from the dataset was initially coded as '?' and so had to changed to NAN values while loading the data from the csv file.
And important attribute, weight which could provide valuable insights to the patient medical data was missing 97% of its data and so had be dropped from the dataset.
payer_code attribute which related to the patient insurance also had considerable values missing and also needed to be removed from the dataset 
Attributes - race, medical_speciality, diag_1, diag_2, and diag_3 had missing values so records which had these missing values were also removed from the dataset
There were multiple hospital encounters for a patient and so duplicate records related to a patients were also removed.

## Exploratory Data Analysis

Assessing the patients demographics show that majority of the patients where between 70-80 years of age and had slightly more female patients than male patients. 
Majority of the patients spents around 1-3 days in the hospital and had taken between 10 to 20 medications and had 9 number of diagnoses

All the numerical data from the dataset could be binned to fewer categories for better analysis

admission_source attribute was removed as it had high corelation with admission_type. And change attribute was also removed as it was highly corelated with insulin

diag_1, diag_2 and diag_3 had high cardinality (around 700) and so were re-coded with the corresponding ICD-9 code ranges to bring down the cardinality.

## Models
As this is a classification problem we will initially try to model using Random forest as this algorithm works well with multiclass classification. The accuracy was 64.7% with f1 score of 56.8%

Modelling using Pycaret came up with Gradient Boosting, Light Gradient Boosting Machine (Light GBM) and CatBoost classifer has top three best models with 65.36%, 65.35% and 65.31% accurancy respectively. And Extreme Gradient Boosting(xgboost) had the best recall value of 38.22% and 65.10% accuracy

Tuning these models further it not produce a better value for CatBoost. 
Tuned Light GBM accuracy increased to 65.43% and xgboost accuracy also increased to 65.44%

## Conclusion
xgboost model had the best prediction with an accuracy of 65.55% and f1 score of 58.34%.
The most important feature that was shown was number of times the patient was admitted as an inpatient patient prior to the current hospital encounter. 

## Future Improvements
- Instead of a multiclass classification, we could attempt to solve this problem as a binary classification, so as to get a better balanced dataset. This may improve our chances of getting a better accuracy with our models

- Selecting better feature subsets according to industry knowledge to create better models

## Acknowledgements
I want to thank my mentor, Raghunandan Patthar who had patiently guided me in gleaning better categories from the dataset and providing with timely and relevant feedbacks. 


