## Exploratory Data Analysis Project 1
This assignment uses data from the UC Irvine Machine Learning Repository, a popular repository for machine learning datasets. In particular, we will be using the “Individual household electric power consumption Data Set” which I have made available on the course web site:
Dataset:
[Electric power consumption](https://d396qusza40orc.cloudfront.net/exdata%2Fdata%2Fhousehold_power_consumption.zip) [20Mb]
</br>Description: Measurements of electric power consumption in one household with a one-minute sampling rate over a period of almost 4 years. Different electrical quantities and some sub-metering values are available.
```R
library("data.table")
setwd("~/Desktop/datasciencecoursera/4_Exploratory_Data_Analysis/project/data")
#Reads in data from file then subsets data for specified dates
powerDT <- data.table::fread(input = "household_power_consumption.txt"
                             , na.strings="?"
                             )
# Prevents histogram from printing in scientific notation
powerDT[, Global_active_power := lapply(.SD, as.numeric), .SDcols = c("Global_active_power")]
# Change Date Column to Date Type
powerDT[, Date := lapply(.SD, as.Date, "%d/%m/%Y"), .SDcols = c("Date")]
# Filter Dates for 2007-02-01 and 2007-02-02
powerDT <- powerDT[(Date >= "2007-02-01") & (Date <= "2007-02-02")]
png("plot1.png", width=480, height=480)
## Plot 1
hist(powerDT[, Global_active_power], main="Global Active Power", 
     xlab="Global Active Power (kilowatts)", ylab="Frequency", col="Red")

 dev.off()
 ```
 ![](https://github.com/mGalarnyk/datasciencecoursera/blob/master/4_Exploratory_Data_Analysis/project/plot1.png)
 ![](https://github.com/mGalarnyk/datasciencecoursera/blob/master/4_Exploratory_Data_Analysis/project1/plot1.png)
 ```R
 library("data.table")

 @@ -61,7 +61,7 @@ plot(x = powerDT[, dateTime]

 dev.off()
 ```
 ![](https://github.com/mGalarnyk/datasciencecoursera/blob/master/4_Exploratory_Data_Analysis/project/plot2.png)
 ![](https://github.com/mGalarnyk/datasciencecoursera/blob/master/4_Exploratory_Data_Analysis/project1/plot2.png)
 ```R
 library("data.table")

 @@ -94,7 +94,7 @@ legend("topright"

 dev.off()
 ```
 ![](https://github.com/mGalarnyk/datasciencecoursera/blob/master/4_Exploratory_Data_Analysis/project/plot3.png)
 ![](https://github.com/mGalarnyk/datasciencecoursera/blob/master/4_Exploratory_Data_Analysis/project1/plot3.png)
 ```R
 library("data.table")

 @@ -139,4 +139,4 @@ plot(powerDT[, dateTime], powerDT[,Global_reactive_power], type="l", xlab="datet

 dev.off()
 ```
 ![](https://github.com/mGalarnyk/datasciencecoursera/blob/master/4_Exploratory_Data_Analysis/project/plot4.png)
 ![](https://github.com/mGalarnyk/datasciencecoursera/blob/master/4_Exploratory_Data_Analysis/project1/plot4.png)
