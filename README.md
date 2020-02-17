# Human Activity Recognition


<img src = https://github.com/yatscool007/Human-Activity-Detection-/blob/master/Images'/res1.PNG>





This project is to build a model that predicts the human activities such as Walking, Walking_Upstairs, Walking_Downstairs, Sitting, Standing or Laying.

This dataset is collected from 30 persons(referred as subjects in this dataset), performing different activities with a smartphone to their waists. The data is recorded with the help of sensors (accelerometer and Gyroscope) in that smartphone. This experiment was video recorded to label the data manually.

## How data was recorded

By using the sensors(Gyroscope and accelerometer) in a smartphone, they have captured '3-axial linear acceleration'(_tAcc-XYZ_) from accelerometer and '3-axial angular velocity' (_tGyro-XYZ_) from Gyroscope with several variations. 

> prefix 't' in those metrics denotes time.

> suffix 'XYZ' represents 3-axial signals in X , Y, and Z directions.

# Quick overview of the dataset :

* Accelerometer and Gyroscope readings are taken from 30 volunteers(referred as subjects) while performing the following 6 Activities.

    1. Walking     
    2. WalkingUpstairs 
    3. WalkingDownstairs 
    4. Standing 
    5. Sitting 
    6. Lying.


* Readings are divided into a window of 2.56 seconds with 50% overlapping. 

* Accelerometer readings are divided into gravity acceleration and body acceleration readings,
  which has x,y and z components each.

* Gyroscope readings are the measure of angular velocities which has x,y and z components.

* Jerk signals are calculated for BodyAcceleration readings.

* Fourier Transforms are made on the above time readings to obtain frequency readings.

* Now, on all the base signal readings., mean, max, mad, sma, arcoefficient, engerybands,entropy etc., are calculated for each window.

* We get a feature vector of 561 features and these features are given in the dataset.

* Each window of readings is a datapoint of 561 features.

## Problem Framework

* 30 subjects(volunteers) data is randomly split to 70%(21) test and 30%(7) train data.
* Each datapoint corresponds one of the 6 Activities.

## Problem Statement

 + Given a new datapoint we have to predict the Activity
 
 
 ## Approach:
 __Data Cleaning__: 
 Checking for duplicate values,checking for duplicate values ,checking for data imbalance 
 
 __Exploratory Data Analysis__:
  <br>- __Feature engineering from domain knowledge__:
      + __Static and Dynamic Activities__

    - In static activities (sit, stand, lie down) motion information will not be very useful.
	- In the dynamic activities (Walking, WalkingUpstairs,WalkingDownstairs) motion info will be significant.

__Applying TSNE to visualize in 2-D__:



__Modelling__:
- __ML Models__:following ML models are implemented and hyperparameter tuning is performed using GridSearchCV to avoid overfitting of data :

- Logisitc Regression
- Linear SVC
- Rbf SVM Classifier
- Decision Tree
- Random Forest
- Gradient Boosted Decision Trees
__Results of ML models__:


### Deep Learning models:
__Model 1:  LSTM(32) + Batchnormalization + Dropout(0.3) + RmsProp__ -

__Model 2:  LSTM(80 cells) + LSTM (35 cells) + Dropout(0.4) +Dropout(0.2) + 1 BatchNormalization layers + Adam Optimizer__ -

__Model 3:  Conv1d(64) +Conv1d(48) +Maxpooling(2) + Batchnormalization + Dropout(0.5) +Dense(100)__ - 

__Model 4:  LSTM(100) + Dropout(0.7) + LSTM(50) + Dropout(0.7) + RmsProp__ - 

## Results


## Improving the results:
link - https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5949027/

As to improve the results and achieve a better accuracy on test data ,I have referred to this research paper and tried to implement the Divide and Conquer Approach in which we perform:
- Two class classification of static and dynamic activities
- Separately classifying static and Dynamic activities as 3 class classification problem 
- Stacking the model to get final output

__Results after Divide and Conquer approach_:


