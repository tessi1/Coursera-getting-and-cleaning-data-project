# Coursera-getting-and-cleaning-data-project
The script run_analysis.R does the following steps

    For creating a tidy data set of wearable computing data originally from http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones
Files that are part of this repo

    README.md -- This file that is being read right now.
    run_analysis.R -- actual R code
    CodeBook.md -- Describes variables, the data and transformations
    
In Order to run this script, you need the library plyr installed
run_analysis.R What this code does?

 1. Merges the training and the test sets to create one data set. 2. Extracts only the measurements on the mean and standard deviation for each measurement. 3. Uses descriptive activity names to name the activities in the data set 4. Appropriately labels the data set with descriptive activity names. 5. Creates a second, independent tidy data set with the average of each variable for each activity and each subject.

It should run in a folder of the Samsung data (the zip had this folder: UCI HAR Dataset) The script assumes requires in it's working directory the following files and folders:

    activity_labels.txt
    features.txt
    test/
    train/

The output is created in a working directory named tidy2.txt


The steps involved are.

    Step 1:
        Read all the test and training files: y_test.txt, subject_test.txt and X_test.txt.
        Combine the files to a data frame in the form of subjects, labels, the rest of the data.

    Step 2:
        Read the features from features.txt and filter it to only retain features that are either means ("mean()") or standard deviations ("std()"). The reason for leaving out meanFreq() is that the goal for this step is to only include means and standard deviations of measurements.
        A new data frame is then created that includes subjects, labels and the described features.

    Step 3:
        Read the activity labels from activity_labels.txt and replace the numbers with the text.

    Step 4:
        Make a column list (including "subjects" and "label" at the start)
        Tidy the list by removing all non-alphanumeric characters and converting the result to lowercase
        Apply the cleaned columnnames to the data frame

    Step 5:
        Create a new data frame by finding the mean for each combination of subject and label. It's done by aggregate() function

    Final step:
        Write the new tidy set into a text file called tidy2.txt, formatted similar to the original files.

