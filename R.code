## test data:
xtest<- read.table("UCI HAR Dataset/test/X_test.txt")
ytest<- read.table("UCI HAR Dataset/test/Y_test.txt")
SubjectTest <-read.table("UCI HAR Dataset/test/subject_test.txt")

## train data:
xtrain<- read.table("UCI HAR Dataset/train/X_train.txt")
ytrain<- read.table("UCI HAR Dataset/train/Y_train.txt")
SubjectTrain <-read.table("UCI HAR Dataset/train/subject_train.txt")

## features and activity
features<-read.table("UCI HAR Dataset/features.txt")
activity<-read.table("UCI HAR Dataset/activity_labels.txt")

##Part1 - merges train and test data in one dataset (full dataset at the end)
x<-rbind(XTest, XTrain)
y<-rbind(YTest, YTrain)
subject<-rbind(SubjectTest, SubjectTrain)
dim(X)
index <- grep("mean\\(\\)|std\\(\\)", features[,2])
x <- x[,index]
names<-features[index,2]
names(x) <- names
names(subject) <- "SubjectID"
names(y) <- "activity"

CleanData <- cbind(Subject, Y, X)
CleanData<-data.table(CleanData) ## here I used data.table package which I installed
tidydata <- CleanData[,lapply(.SD, mean), by = 'SubjectID,activity']
head(tidydata[order(SubjectID)][,c(1:4)], 12)
