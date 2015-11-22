# xtest is a data frame where I put the Xtest data
# ytest is a data frame where I put the Y labels
# subtest is a data frame where I put subset
# xtrain is a data frame where I put the Xtrain data
# ytrain is a data frame where I put the Y labels
# subtrain is a data frame where I put subset
# in act_lab I put the activity lab
# in feat I put the features
# in test and train I put the bind file
# in unique_files I put the merge between test and train
# mean_sd is a file where I put the value with mean or SD
# finaly write the test file

xtest<-read.table("X_test.txt") #read the Xtest data from file downloaded
ytest<-read.table("y_test.txt") #read the labels for Xtest
subtest<-read.table("subject_test.txt") #read the subset for test

xtrain<-read.table("X_train.txt") #read the Xtrain data from file downloaded
ytrain<-read.table("y_train.txt") #read the labels for Xtrain
subtrain<-read.table("subject_train.txt") #read the subset for train

act_lab<-read.table("activity_labels.txt") #read activity lab
feat<-read.table("features.txt") #read features

test<-cbind(xtest,ytest,subtest) #cbind of 3 file test
train<-cbind(xtrain, ytrain, subtrain) #cbind of 3 file train

unique_file<-rbind(test,train) #rbind to have unique file merged

mean_sd<- unique_file [ which(unique_file$gender=='main' | unique_file$age =='std'), ]

tidy_data<-unique_file

write.table(tidy_data, "tidy_data.txt",row.names=FALSE) #tidy data file wrtitten on directory
