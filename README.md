# Personalized-Cancer-Diagosis: Project Overview 
* Personalized Medicine Redefining Cancer Treatment is a real world data set from Kaggle
* Memorial Sloan Kettering Cancer Center (MSKCC) launched this competition, accepted by the NIPS 2017 Competition Track, because we need your help to take personalized medicine   to its full potential
* Classify the given genetic variations/mutations based on evidence from text-based clinical literature.
* Optimized Naive Bayes,Logistic Regression,Linear SVM and Random Forest Regressors to reach the best model. 

## Code and Resources Used 
**Python Version:** 3.7  
**Packages:** pandas, numpy, sklearn, matplotlib, seaborn,pickle,re,nltk

## Dataset
* Id: The id of the row used to link the mutation to the clinical evidence (Numerical)
* Gene: The gene where this genetic mutation is located (Categorical)
* Variants: The aminoacid change for this mutations (Categorical)
* Text: Text collected from the clinical evidences (Text)
* Class: 1-9 the class this genetic mutation has been classified on (Numeric)
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
I looked at the distributions of the data and the value counts for the various categorical variables and evaluate univariate analyses for each features. Below are a few highlights from the pivot tables. 

![alt text](https://github.com/vaibhavt14/Personalized-Cancer-Diagosis/blob/main/class_distribution.png "Class features for target variable")
![alt text](https://github.com/vaibhavt14/Personalized-Cancer-Diagosis/blob/main/histogram.png "train data for univariate analysis")

## Model Building 

First, I transformed the text variables into machine learning models. I also split the data into train,tests and validation sets with a test size of 20%.   

I tried different models and evaluated them using Multi class logg-loss and compare the logg-loss for each train,test,cross-validation  

## Model performance
The Logistic model far outperformed the other approaches on the test and validation sets. 
*	**Logistic Regression** : Log loss(Test data) = 1.048
*	**Naive Bayes**: Log loss(Test data) = 1.21
*	**Linear SVM**: Log loss(Test data) = 1.063



