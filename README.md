# Alphabet-Soup
algorithm to predict funding to non-profits

## Introduction
This project is using deep learning, neural networks, to predict funding for charities.  Alphabet soup a non-profit foundation wants to create an algorithm to predict whether or not applicants for funding will be successful.  The model will use the features in the dataset for creation of a binary classifer capable of predicting whether applicants will be successful if funded by Alphabet Soup. 

## Methods
A csv containing more than 34,000 organizations that have recieved funding from Alphabet Soup over the years was utilized.  The dataset containg the following columns in the metadata:

  *EIN and NAME—Identification columns

  *APPLICATION_TYPE—Alphabet Soup application type

  *AFFILIATION—Affiliated sector of industry

  *CLASSIFICATION—Government organization classification

  *USE_CASE—Use case for funding

  *ORGANIZATION—Organization type

  *STATUS—Active status

  *INCOME_AMT—Income classification

  *SPECIAL_CONSIDERATIONS—Special consideration for application

  *ASK_AMT—Funding amount requested

  *IS_SUCCESSFUL—Was the money used effectively
  
First steps in model creation was preprocessing of the data.  The csv was read in utilizing Pandas.  The EIN and NAME columns were dropped from the dataset.  The number of unique values for each column.  For columns with more than 10 unique values were binned.  pd.get_dummmies() was utilized to encode categorical variables.  Data was scaled using StandardScaler.  Next a deep learning model was created by assigning the number of inpiut features and nodes for each layer using Tensorflow Keras. The model was then compiled and trained.  
![compile train 1](https://user-images.githubusercontent.com/88807979/155920653-c57244ad-43c0-4316-a37c-5b5b86e33b42.png)

The model was then evaluated using the test data to determine the loss and accuracy.  The results were saved and exported to an HDF5 file. 
![evaluate 1](https://user-images.githubusercontent.com/88807979/155920671-4cfa92e7-92dc-497a-9081-a18afa53cedb.png)

An attempt to optimize the model was made using Keras tuning and hyper parameters.  
![optimization 1](https://user-images.githubusercontent.com/88807979/155921181-5bc25b0d-f03f-4364-aa44-25f22f799026.png)
![optimization 2](https://user-images.githubusercontent.com/88807979/155921192-a8adf180-6009-4fd8-a009-7077c0669517.png)

## Results
The original sequential model was 3 layers.  The hidden layers were ReLU activated.  Total parameters were 5,981.  Accuracy 72.9% and Loss 56.0%
Kerastuner best model was 5 first units and 1 number layer.  Layers were ReLU activated. Accuracy 72.9% and Loss 55.0%

## Discussion
The target variable in the model was IS_SUCCESSFUL.  All other columns not removed in preprocessing were used as features.  The columns removed in preprocessing were the EIN and NAME both of which add no value to predicting if an organization will be successful.  I was unable to obtain the target of greater than 75% accuracy.  The simple model with two hidden layers was comparable to the KerasTuner model.  Some features may have more weight in determining if an organization is successful.  Detemining which of those features to feed into the model would make it a stronger and more predictive model.  
