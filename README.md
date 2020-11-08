# Personalized-Cancer-Diagosis: Project Overview 
* Personalized Medicine Redefining Cancer Treatment is a real world data set from Kaggle
* Memorial Sloan Kettering Cancer Center (MSKCC) launched this competition, accepted by the NIPS 2017 Competition Track, because we need your help to take personalized medicine   to its full potential
* Classify the given genetic variations/mutations based on evidence from text-based clinical literature.
* Optimized Naive Bayes,Logistic Regression,Linear SVM and Random Forest Regressors to reach the best model. 

## Code and Resources Used 
**Python Version:** 3.7  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn,pickle,re,nltk
**For Web Framework Requirements:**  ```pip install -r requirements.txt```   

## Dataset
* Features
<ul>
<li>Id: The id of the row used to link the mutation to the clinical evidence (Numerical)</li>
<li>Gene:  The gene where this genetic mutation is located (Categorical)</li>
<li>Variants: The aminoacid change for this mutations (Categorical)</li>
<li>Text: Text collected from the clinical evidences (Text)</li>
<li>Class: 1-9 the class this genetic mutation has been classified on (Numeric)</li>
</ul>
* Number of data points in train data: 2124
* Number of data points in test data: 665
* Number of data points in cross validation data: 532

## Data Cleaning
After understanding of business requirements, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

*	Clean the text features using nltk package such as removing punctuations
*	Convert Gene features to one hot encoding(247-Dimensions)
*	Convert Variants features to one hot encoding(2266-Dimensions)
*	Convert Text features to one hot encoding for top 2500 tf-idf words (2500-Dimensions)


## EDA
I looked at the distributions of the data and the value counts for the various categorical variables. Below are a few highlights from the pivot tables. 

![alt text](https://github.com/PlayingNumbers/ds_salary_proj/blob/master/salary_by_job_title.PNG "Salary by Position")
![alt text](https://github.com/PlayingNumbers/ds_salary_proj/blob/master/positions_by_state.png "Job Opportunities by State")
![alt text](https://github.com/PlayingNumbers/ds_salary_proj/blob/master/correlation_visual.png "Correlations")

## Model Building 

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.   

I tried three different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.   

I tried three different models:
*	**Multiple Linear Regression** – Baseline for the model
*	**Lasso Regression** – Because of the sparse data from the many categorical variables, I thought a normalized regression like lasso would be effective.
*	**Random Forest** – Again, with the sparsity associated with the data, I thought that this would be a good fit. 

## Model performance
The Random Forest model far outperformed the other approaches on the test and validation sets. 
*	**Random Forest** : MAE = 11.22
*	**Linear Regression**: MAE = 18.86
*	**Ridge Regression**: MAE = 19.67

## Productionization 
In this step, I built a flask API endpoint that was hosted on a local webserver by following along with the TDS tutorial in the reference section above. The API endpoint takes in a request with a list of values from a job listing and returns an estimated salary. 



