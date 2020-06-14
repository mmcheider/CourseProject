---
title: "Codebook for Tidy Dataset"
author: "Ming-Mei Heider"
date: "6/14/2020"
output:
  html_document: 
  keep_md: yes
---


## Project Description

This project is to prepare tidy data that can be used for later analysis. The 
tidy data set is created with the average of each variable for each activity and
each subject.


### Collection of the raw data

The original features selected for Human Activity Recognition dataset come from 
the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. The 
acceleration signal was then separated into body and gravity acceleration 
signals (tBodyAcc-XYZ and tGravityAcc-XYZ).The body linear acceleration and 
angular velocity were derived in time to obtain Jerk signals (tBodyAccJerk-XYZ 
and tBodyGyroJerk-XYZ). In addition, the magnitude of these three-dimensional 
signals were calculated using the Euclidean norm (tBodyAccMag, tGravityAccMag, 
tBodyAccJerkMag, tBodyGyroMag, tBodyGyroJerkMag). At last, a Fast Fourier 
Transform (FFT) was applied to some of these signals producing fBodyAcc-XYZ, 
fBodyAccJerk-XYZ, fBodyGyro-XYZ, fBodyAccJerkMag, fBodyGyroMag, 
fBodyGyroJerkMag. (Note the 't' to indicate time domain signals, and the 'f' to 
indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each 
pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

tBodyAcc-XYZ
tGravityAcc-XYZ
tBodyAccJerk-XYZ
tBodyGyro-XYZ
tBodyGyroJerk-XYZ
tBodyAccMag
tGravityAccMag
tBodyAccJerkMag
tBodyGyroMag
tBodyGyroJerkMag
fBodyAcc-XYZ
fBodyAccJerk-XYZ
fBodyGyro-XYZ
fBodyAccMag
fBodyAccJerkMag
fBodyGyroMag
fBodyGyroJerkMag

The variable that was estimated from these signals in this tidy dataset is: 
mean(): Mean value

For more information, please see
http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones


### Guide to create the tidy data file

The steps to create the tidy data file are:

 1. download the the Samsung data from 
    http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones
    or https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip,
    extract all files and saved them in a folder called "UCI HAR Dataset" in 
    your working directory
 2. execute the run_analysis.R script in an enviroment that can interpret R 
    scripts.
 3. verify that "tidy_dataset.txt" (tidy data file) is generated in your working
    directory after running script successfully.


### Cleaning of the data

The R script "run_analysis.R" is created to perform the following,

- Merges the training and the test sets to create one data set.
- Extracts only the measurements on the mean and standard deviation for each 
  measurement.
- Uses descriptive activity names to name the activities in the data set
- Appropriately labels the data set with descriptive variable names.
- Creates a second, independent tidy data set with the average of each variable 
  for each activity   and each subject.


### Description of the variables in the tidy_dataset.txt file

- Dimensions of the dataset: 11880 obs. of 4 variables
- Variables present in the dataset: 
  1. SubjectId
  2. Activity
  3. Measurement
  4. Average
  
- Summary of the data: 

 |SubjectId    |   Activity             |  Measurement     |    Average      |
 |:------------|:-----------------------|:-----------------|:----------------|
 |Min.   : 1.0 | WALKING           :1980| Length:11880     | Min.   :-0.99767|  
 |1st Qu.: 8.0 | WALKING_UPSTAIRS  :1980| Class :character | 1st Qu.:-0.96205| 
 |Median :15.5 | WALKING_DOWNSTAIRS:1980| Mode  :character | Median :-0.46989|
 |Mean   :15.5 | SITTING           :1980|                  | Mean   :-0.48436|
 |3rd Qu.:23.0 | STANDING          :1980|                  | 3rd Qu.:-0.07836|
 |Max.   :30.0 | LAYING            :1980|                  | Max.   : 0.97451|
 
 
### Variable 1 - SubjectId

It identifies the subject who performed the activity for each window sample. 

- Class of the variable: integer vector
- Unique values/levels of the variable: range from 1 to 30
- Unit of measurement 


### Variable 2 - Activity

It links the class labels with their activity name.

- Class of the variable: factor vector with 6 levels
- Unique values/levels of the variable: "WALKING","WALKING_UPSTAIRS",
  "WALKING_DOWNSTAIRS","SITTIN","STANDING","LAYING"
- Unit of measurement


### Variable 3 - Measurement

Measurement from the sensor signals (accelerometer and gyroscope) with time and 
frequency domain variables.

 - Class of the variable: character vector 
 - Unique values/levels of the variable:
   "TimeBodyAcc-mean-X"               
   "TimeBodyAcc-mean-Y"                "TimeBodyAcc-mean-Z"               
   "TimeBodyAcc-std-X"                 "TimeBodyAcc-std-Y"                
   "TimeBodyAcc-std-Z"                 "TimeGravityAcc-mean-X"            
   "TimeGravityAcc-mean-Y"             "TimeGravityAcc-mean-Z"            
   "TimeGravityAcc-std-X"              "TimeGravityAcc-std-Y"             
   "TimeGravityAcc-std-Z"              "TimeBodyAccJerk-mean-X"           
   "TimeBodyAccJerk-mean-Y"            "TimeBodyAccJerk-mean-Z"           
   "TimeBodyAccJerk-std-X"             "TimeBodyAccJerk-std-Y"            
   "TimeBodyAccJerk-std-Z"             "TimeBodyGyro-mean-X"              
   "TimeBodyGyro-mean-Y"               "TimeBodyGyro-mean-Z"              
   "TimeBodyGyro-std-X"                "TimeBodyGyro-std-Y"               
   "TimeBodyGyro-std-Z"                "TimeBodyGyroJerk-mean-X"          
   "TimeBodyGyroJerk-mean-Y"           "TimeBodyGyroJerk-mean-Z"          
   "TimeBodyGyroJerk-std-X"            "TimeBodyGyroJerk-std-Y"           
   "TimeBodyGyroJerk-std-Z"            "TimeBodyAccMag-mean"              
   "TimeBodyAccMag-std"                "TimeGravityAccMag-mean"           
   "TimeGravityAccMag-std"             "TimeBodyAccJerkMag-mean"          
   "TimeBodyAccJerkMag-std"            "TimeBodyGyroMag-mean"             
   "TimeBodyGyroMag-std"               "TimeBodyGyroJerkMag-mean"         
   "TimeBodyGyroJerkMag-std"           "FrequencyBodyAcc-mean-X"          
   "FrequencyBodyAcc-mean-Y"           "FrequencyBodyAcc-mean-Z"          
   "FrequencyBodyAcc-std-X"            "FrequencyBodyAcc-std-Y"           
   "FrequencyBodyAcc-std-Z"            "FrequencyBodyAccJerk-mean-X"      
   "FrequencyBodyAccJerk-mean-Y"       "FrequencyBodyAccJerk-mean-Z"      
   "FrequencyBodyAccJerk-std-X"        "FrequencyBodyAccJerk-std-Y"       
   "FrequencyBodyAccJerk-std-Z"        "FrequencyBodyGyro-mean-X"         
   "FrequencyBodyGyro-mean-Y"          "FrequencyBodyGyro-mean-Z"         
   "FrequencyBodyGyro-std-X"           "FrequencyBodyGyro-std-Y"          
   "FrequencyBodyGyro-std-Z"           "FrequencyBodyAccMag-mean"         
   "FrequencyBodyAccMag-std"           "FrequencyBodyBodyAccJerkMag-mean" 
   "FrequencyBodyBodyAccJerkMag-std"   "FrequencyBodyBodyGyroMag-mean"    
   "FrequencyBodyBodyGyroMag-std"      "FrequencyBodyBodyGyroJerkMag-mean"
   "FrequencyBodyBodyGyroJerkMag-std" 
  - Unit of measurement: 128 readings/window

##### Notes on variable 3:

Please see the description of "Collection of the raw data" for how each 
measurement is constructed.
 
 
### Variable 4 - Average

It shows average of each measurement for each activity and each subject. 

 - Class of the variable: numeric vector
 - Unique values/levels of the variable: range from -0.99767 to 0.97451
 - Unit of measurement


 

