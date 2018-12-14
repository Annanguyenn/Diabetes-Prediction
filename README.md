# Diabetes Prediction

Trained and compared the performance of the machine learning models with two different missing-data imputation: mean imputation and guess matrix. 

Tools: Python, Scikit-Learn, Logistic Regression, Random Forest Classifier, AdaBoost, Perceptron.

**Data:**

Data Source: `diabetesdata.csv`. About the data:

1. __TimesPregnant__: Number of times pregnant 
2. __glucoseLevel__: Plasma glucose concentration a 2 hours in an oral glucose tolerance test 
3. __BP__: Diastolic blood pressure (mm Hg)  
5. __insulin__: 2-Hour serum insulin (mu U/ml) 
6. __BMI__: Body mass index (weight in kg/(height in m)^2) 
7. __pedigree__: Diabetes pedigree function 
8. __Age__: Age (years) 
9. __IsDiabetic__: 0 if not diabetic or 1 if diabetic) 

**Summary:** 

First, I use the dataset with Mean imputation to train perceptron, logistic regression and random forest models using 15% test split and report the train and test accuracy.

Second, instead of generalizing the NAN values with the mean of the feature, I assigned values to NANs based on some hypothesis. For example for age I assume that the relation between BMI and BP of people is a reflection of the age group. I can have 9 types of BMI and BP relations and my aim is to find the median age of each of that group:

The Age guess matrix I used look like this:  

| BMI | 0       | 1      | 2  |
|-----|-------------|------------- |----- |
| BP  |             |              |      |
| 0   | a00         | a01          | a02  |
| 1   | a10         | a11          | a12  |
| 2   | a20         | a21          |  a22 |


Then I created a guess_matrix  for NaN values of *'Age'* ( using 'BMI' and 'BP')  and  *'glucoseLevel'*  (using 'BP' and 'Pedigree') for the given dataset and assign values accordingly to the NaNs in 'Age' or *'glucoseLevel'* .__

Use this dataset (with all features in categorical form) to train perceptron, logistic regression and random forest models using 15% test split. And then I compared the performance with the previous ones.

Notes:
Mean imputation is not the best type of imputation to use. Because it has several problems such as:
* Mean imputation reduces the variance of the imputed variables.
* Mean imputation shrinks standard errors, which invalidates most hypothesis tests and the calculation of confidence interval.
* Mean imputation does not preserve relationships between variables such as correlations.

Alternative methods to impute data: Paul Allison (2009) suggests either maximum likelihood estimation or multiple imputation methods, both of which try to preserve relationships between variables and the inherent variability of the data. Stochastic regression imputation: The predicted value from a regression plus a random residual value.This has all the advantages of regression imputation but adds in the advantages of the random component. Most multiple imputation is based off of some form of stochastic regression imputation.

Please find the attached files for more details. 

Thank you!
