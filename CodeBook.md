This code book will describe the variables, data, and any transformations or work that was performed to clean up the data.
The run_analysis.R script performs the data preparation and then followed by the 5 steps required as described in the course project’s definition.

Download the dataset from the given link.

Dataset was downloaded and extracted under the folder called UCI HAR Dataset

Assign each data to variables as described below.

features <- features.txt 
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.

activities <- activity_labels.txt 
The list of activities performed when the corresponding measurements were taken and its codes (labels)

subject_test <- test/subject_test.txt  
This contains test data of 9/30 volunteer test subjects being observed.

x_test <- test/X_test.txt  
This contains recorded features test data.

y_test <- test/y_test.txt  
This table contains test data of activities’code labels.

subject_train <- test/subject_train.txt  
This table contains train data of 21/30 volunteer subjects being observed.

x_train <- test/X_train.txt  
This table contains recorded features train data.

y_train <- test/y_train.txt  
This tablecontains train data of activities’code labels.

Following steps describe merging the training and the test sets to create one data set.

X  is created by merging x_train and x_test using rbind() function.

Y  is created by merging y_train and y_test using rbind() function.

Subject  is created by merging subject_train and subject_test using rbind() function.

Merged_Data is created by merging Subject, Y and X using cbind() function

To extract only the measurements on the mean and standard deviation for each measurement.
TidyData  is created by subsetting Merged_Data, selecting only columns: subject, code and the measurements on the mean and standard deviation (std) for each measurement

Uses descriptive activity names to name the activities in the data set
Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the  activities variable.

Appropriately labels the data set with descriptive variable names
code column in TidyData renamed into activities.

All Acc in column’s name replaced by Accelerometer.
All Gyro in column’s name replaced by Gyroscope
All BodyBody in column’s name replaced by Body
All Mag in column’s name replaced by Magnitude
All start with character f in column’s name replaced by Frequency
All start with character t in column’s name replaced by Time

From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject
FinalData  is created by sumarizing TidyData taking the means of each variable for each activity and each subject, after groupped by subject and activity.
Export FinalData into FinalData.txt file.
