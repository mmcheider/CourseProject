#
# Description: The goal of this project is to prepare a tidy data that can be 
#              used for later analysis. The data was obtained from 
#              http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones
#              and it represented data collected from the accelerometers from 
#              the Samsung Galaxy S smartphone.

# Packages used in the script
library(dplyr)
library(tidyr)

# Step 1. Merges the training and the test sets to create one data set.
#    - Training and test data sets are stored in .txt file format. 
#    - They are read in as dataframes, and then merged into one dataframe.

testdata <- read.table("./UCI HAR Dataset/test/X_test.txt")
traindata <- read.table("./UCI HAR Dataset/train/X_train.txt")
mydata <- bind_rows(traindata, testdata)

# Step 2. Extracts only the measurements on the mean and standard deviation for each 
#    measurement.
#    - Read in all features of the original data set and store them in a data 
#      frame
#    - Search for the measurements on the mean and standard deviation
#    - 'meanFreq' measurements are NOT considered as mean measurements and are
#      excluded in the selection
#    - Label all variables' names by setting the column names

features <- read.table("./UCI HAR Dataset/features.txt", 
                       stringsAsFactors = FALSE)
tmp1 <- grep("mean|std", features$V2, ignore.case = FALSE, value = TRUE)
tmp2 <- grep("meanFreq",features$V2, ignore.case = FALSE, value = TRUE)
colnames(mydata) <- features[,2]
mydata1 <- select(mydata, tmp1, -tmp2)

# Step 3. Uses descriptive activity names to name the activities in the data set
#    - Read in activity labels and merge into one data frame for training and 
#      test data.  
#    - Merge the above data frame with step 2 data frame.
#    - Read in the .txt file which links the class labels with their activity 
#      name.
#    - Use the descriptive activity name to name the activities.

testactivity <- read.table("./UCI HAR Dataset/test/Y_test.txt")
trainactivity <- read.table("./UCI HAR Dataset/train/Y_train.txt")
mydata2 <- bind_rows(trainactivity, testactivity)
colnames(mydata2) <- "Activity"
mydata3 <- bind_cols(mydata2, mydata1)
activity_label <- read.table("./UCI HAR Dataset/activity_labels.txt")
mydata3$Activity <- factor(mydata3$Activity, levels = activity_label$V1, 
                           labels=activity_label$V2)

# Step 4. Appropriately labels the data set with descriptive variable names.
#    - Use "Time" to replace "t" to indicate time domain signals in the variable 
#      names
#    - Use "Frequency" to replace "f" to indicate frequency domain signals in 
#      the variable names
#    - Remove "()" in the variable names 
#    - Read in subject data and merge with previous data frame to create a 
#      appropriately labelled data set

colnames(mydata3) <- gsub("^t", "Time", colnames(mydata3)) 
colnames(mydata3) <- gsub("^f", "Frequency", colnames(mydata3)) 
colnames(mydata3) <- gsub("\\(\\)", "", colnames(mydata3))
testsubject <- read.table("./UCI HAR Dataset/test/subject_test.txt")
trainsubject <- read.table("./UCI HAR Dataset/train/subject_train.txt")
mydata4 <- bind_rows(trainsubject, testsubject)
colnames(mydata4) <- "SubjectId"
whole <- bind_cols(mydata4, mydata3)

# Step 5. From the data set in step 4, creates a second, independent tidy data set 
#    with the average of each variable for each activity and each subject.
#    - The tidy data set has four variables: SubjectID, Activity, Measurement, 
#      and Average (for each measurement).
#    - The column names of the data set in step 4 become data values of 
#      "Measurement" variable in this data set.

whole <- whole %>% group_by(SubjectId, Activity) %>%
     summarise_each(funs(mean)) %>%
     gather(key = "Measurement", value = "Average", -c(SubjectId, Activity)) %>%
     arrange(Activity, .by_group = TRUE)

# Step 6. Write the second tidy data set to 'tidy_dataset.txt' file

write.table(whole, "tidy_dataset.txt", row.name = FALSE)

