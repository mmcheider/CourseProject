---
title: "ReadMe"
author: "Ming-Mei Heider"
date: "6/14/2020"
output:
  html_document: 
  keep_md: yes
---


## Description

The goal of this project is to prepare tidy data that can be used for later 
analysis. The data was obtained from http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones 
and it represented data collected from the accelerometers from the Samsung 
Galaxy S smartphone. 

An independent set of data is created with the average of each variable for each
activity and each subject. This tidy data set can be read in and viewed in 
RStudio by running the following commands,

- tidy_data <- read.table("tidy_dataset.txt", header = TRUE)
- View(tidy_data)

There is a file named run_analysis.R in the main directory. The R script code 
can be run if the Samsung data is in the working directory. If this is not the 
case, please go to 
https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
and download the Samsung data. Once it is downloaded, please extract all files 
and save them in a folder called "UCI HAR Dataset" in your working directory.

#### The R script "run_analysis.R" is created to perform the following,

- Step 1. Merges the training and the test sets to create one data set.
    - Training and test data sets are stored in .txt file format. 
    - They are read in as dataframes, and then merged into one dataframe.

- Step 2. Extracts only the measurements on the mean and standard deviation for 
         each measurement.
    - Read in all features of the original data set and store them in a data 
      frame
    - Search for the measurements on the mean and standard deviation
    - 'meanFreq' measurements are NOT considered as mean measurements and are
      excluded in the selection
    - Label all variables' names by setting the column names

- Step 3. Uses descriptive activity names to name the activities in the data set
    - Read in activity labels and merge into one data frame for training and 
      test data.  
    - Merge the above data frame with step 2 data frame.
    - Read in the .txt file which links the class labels with their activity 
      name.
    - Use the descriptive activity name to name the activities.

- Step 4. Appropriately labels the data set with descriptive variable names.
    - Use "Time" to replace "t" to indicate time domain signals in the variable 
      names
    - Use "Frequency" to replace "f" to indicate frequency domain signals in 
      the variable names
    - Remove "()" in the variable names 
    - Read in subject data and merge with previous data frame to create a 
      appropriately labelled data set

- Step 5. From the data set in step 4, creates a second, independent tidy data set 
    with the average of each variable for each activity and each subject.
    - The tidy data set has four variables: SubjectID, Activity, Measurement, 
      and Average (for each measurement).
    - The column names of the data set in step 4 become data values of 
      "Measurement" variable in this data set.

- Step 6. Write the second tidy data set to 'tidy_dataset.txt' file

And this tidy data text file meets the principles of tidy data. According to 
Hadley’s paper, https://www.jstatsoft.org/article/view/v059i10

In tidy data:

1. Each variable forms a column.
2. Each observation forms a row.
3. Each type of observational unit forms a table.


### This project includes the following files:

- 'README.md'

- 'run_analysis.R': prepare and create the tidy data set

- 'cookbook.md': show information about the variables and summaries calculated, 
                 along with units


For more information, please see
http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones


