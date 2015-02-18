---
title: "codebook.md"

---
Introduction:

This output dataset is created from multiple numerical observations obtained during an experiment where individuals (referred onwards as 'subjects') were wearing smartphones and sensor data was recorded during various activities. Specifically, the values were recorded from smartphone's accelerometer and gyroscope sensors. Various transformations were performed on the raw data before it was taken input in the run_analysis.R script.

Objective:

.Merge the training and the test sets to create one data set.
.Extract only the measurements on the mean and standard deviation for each measurement.
.Use descriptive activity names to name the activities in the data set
.Appropriately label the data set with descriptive variable names.
.From the data set in previous step, create a second, independent tidy data set with the average of each variable for each activity and each subject.


Input:

The source of data was: https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip 

From above source, the following files were utilized as input:


features.txt  - The names of features were extracted from this file. 

activity_labels.txt The names of six (6) activites were extracted from this file. 

train/y_train.txt and test/y_test.txt These file contained the activity index for each data value (training and test) 

train/subject_train.txt and test/subject_test.txt These files contained the Subject index for each data value (training and test) 

train/X_train.txt and test/X_test.txt These files contained the actual transformed sensor data for each feature (training and test) 

Method:

The R script utilized the following methods and steps to accomplish the task.

Loading:
.The R script (run_analysis.R) loaded the data in test and training files and merged them using rbind function. 
.The next step was give proper column names from features.txt file. Although it was Task #4 of the project, it was done ahead of time to facilitate Task #2.

Extraction:
.Next, subsetting technique was used to take extract columns which have word "mean" or "std" in them. This created two new data frames called allMeans and allStdev (representing all columns which contain means and all columns which contain standard deviation).

Enrichment:
.Next, the script loads the list of activities and corresponding index (factors) of activity for each data value. Factors are created and their textual representation is then merged in the ongoing dataset.
.The script loads the subjects and corresponding index (factors) of activity for each data value. These subject ids are then merged in the ongoing dataset.

Aggregation
.Data is aggregated to list mean of each feature observation for every subject and activity.

Transformation
.Using tidyr, the data is transformed in a 'normalized' form where features are converted from columns to rows.

Output:
Following is the layout of output file.

Subject: The identifier of Subject for which the observations were recorded. These range for 1 to 30. 

ActivityName The names of activities during which observations were taken. These include six (6) activites: WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, and LAYING. 

Feature: The names of various features of data observed. These are names of transformed values as given in input, but are renamed for more readability.

meanOfFeature: The average of each value of feature observed for given subject and activity. 

