#Merges the training and the test sets to create one data set
#given the names to the col
library(reshape2)
features = read.table("C:/Users/Admin/Desktop/R/d/Dataset/features.txt")
subject1 = read.table("C:/Users/Admin/Desktop/R/d/Dataset/test/subject_test.txt")
test_x = read.table("C:/Users/Admin/Desktop/R/d/Dataset/test/X_test.txt")
test_y = read.table("C:/Users/Admin/Desktop/R/d/Dataset/test/y_test.txt")
subject2 = read.table("C:/Users/Admin/Desktop/R/d/Dataset/train/subject_train.txt")
train_x = read.table("C:/Users/Admin/Desktop/R/d/Dataset/train/X_train.txt")
train_y = read.table("C:/Users/Admin/Desktop/R/d/Dataset/train/y_train.txt")
names(test_x) = features$V2
names(train_x) = features$V2
names(subject1) = "sub"
names(subject2) = "sub"
names(test_y) = "act"
names(train_y) = "act"
f = cbind(subject1,test_x,test_y)
#print(head(f))
g = cbind(subject2,train_x,train_y)
print(head(g))
combined_dataset = rbind(f,g)
data= head(combined_dataset)
print(tail(combined_dataset))
#write.csv(data,"dataset.csv")
######################################################################################
#determing the mean and standard dev
vector1 = grep("mean", names(combined_dataset))
vector2 = grep("std", names(combined_dataset))
meanstd = combined_dataset[,c(vector1,vector2)]
#write.csv(meanstd,"mean_std.csv")
######################################################################################
# convert the activity column from integer to factor and then giving the labels to each activity, descriptive names were given for each variable
combined_dataset$act <- factor(combined_dataset$act, labels=c("Walking",
     "Walking Upstairs", "Walking Downstairs", "Sitting", "Standing","Laying"))
print(combined_dataset$act)
#write.csv((head(combined_dataset,20)),"C:/Users/Admin/Desktop/R/combined.csv")
write.csv(combined_dataset,"C:/Users/Admin/Desktop/R/combined.csv")
##########################################################################################
# create the tidy data set
melted = melt(combined_dataset, id = c("sub","act"))
tidy = dcast(melted, sub+act ~ variable, mean)
#print(head(tidy))
write.csv(tidy, "C:/Users/Admin/Desktop/R/tidy.csv")
##########################################################################################
