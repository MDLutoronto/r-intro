---
title: "Introduction to R"
layout: "home"
description: ""
permalink: "/"  #! Remove this if not the homepage
---

# Introduction to R

This guide is suitable for new R\-users or advanced level R\-users looking for information on specific topics. The topics covered in this guide are importing, exploring, modifying and managing data.

The main dataset used is the flights dataset. It contains the US domestic flights in January 2020 \[1]. The other two datasets used are fabricated datasets created for the purpose of this guide. The link to the recording of this workshop can be found [here](https://play.library.utoronto.ca/watch/23a9188c87a752c5aa2cdd79a4971eb8). Additional resources are listed below. If you need assistance, fill out the [support request form](https://mdl.library.utoronto.ca/research/help). **TABLE OF CONTENTS** 
[Importing Data](#importingdata)  
[Exploring Data](#exploringdata)  
[Graphs](#graphs)  
[New Variables](#newvariables)  
[Managing Data](#managingdata)  
[Resources](#resources)

### 

### **Importing Data**

**Working directory**The directory is the place on your computer that is the home for R; therefore, this is where R is saving files and also where R is looking for files. Because R might be using a folder buried deep in your computer’s hard drive, there are two ways of finding and setting your working directory. First, you can use **getwd()** to find the current directory and **setwd()** to set the directory to a different path. NOTE: need to use the forward (/) instead of the backward slash (\\) for directory paths in R.
```

getwd()
setwd("/Users/nadia/Desktop")
```
 The second way is by going under **File** on the menu bar and going down to **Change dir**. This way is best if you do not know the exact name and location of where you want to set your new working directory because it allows you to go through all of the files on your computer. **Importing Data****DATA**: [flights.csv](https://maps.library.utoronto.ca/workshops/R1/flights.php)

Download the flights dataset by clicking on the link above or using the url *uoft.me/flightscsv*. Use **read.csv()** to read csv files. Set the header option to true if the file has column titles and false otherwise. The default option is always true.
```

flights<-read.csv("January 2020 Flights.csv")
```
 

### 

### **Exploring Data**

Unless you opened the .csv file beforehand, you don’t know much about the information you just loaded into R. To find out more, use the **dim()** function to find out the dimension of a data set. To view to contents of a dataset, use the **str()**function. The **head()** function displays the first six rows of the dataset and **tail()** displays the last six rows.
```

str(flights)
head(flights)
tail(flights)
![str(flights) result]({{ '/assets/images/IntroToR_001.png' | relative_url }})
```
<img src='{{ '/assets/images/IntroToR_002.png' | relative_url }}' alt='head(flights) result' title='' width='901' height='101' />

<img src='{{ '/assets/images/IntroToR_003.png' | relative_url }}' alt='tail(flights) result' title='' width='889' height='96' />

 

To open or, in R terminology, print the content of a data set or a variable in the R\-console, simply write the data set or the variable. A data set has 2 dimensions. The first dimension is the row number and the second dimension is the column number. The two dimensions are separated by a comma. For example, ont14\[1,2] prints the value in the first row and second column of the ont14 data set, ont14\[1, ] prints the first row and ont14\[,2] prints the second column. As you may notice, we use square brackets when isolating data and round brackets when working with functions. To print a range of rows or a range of columns, indicate the range separated by a colon.
```

flights[1,5]
flights[1,"originstate"]
flights[1, 1:5]
flights[1000:1005,c("originstate", "deptime", "depdelay")]
![example code results]({{ '/assets/images/IntroToR_004.png' | relative_url }})
```
 When we type a variable by itself, it gives us an error message. To access a variable, use the dollar sign “$”. For example, flights$originstate returns the originstate variable.
```

originstate
flights$originstate
![Error for originstate]({{ '/assets/images/IntroToR_update1_0.png' | relative_url }})
<img src='{{ '/assets/images/IntroToR_005.png' | relative_url }}' alt='Variable data' title='' width='902' height='275' />
```
 **Frequency Tables** 
The **table()** function can be used to make a frequency table. You will also find functions from external packages that can be used to make frequency tables.
```

table(flights$depdelay)
table(flights$depdelay, exclude=NULL)
![frequency tables]({{ '/assets/images/IntroToR_006.png' | relative_url }})
```
You can use the **CrossTable()** function from the gmodels package to make a two\-way frequency table. First, you need to install the gmodels package using the **install.packages()** function and load it using the **library()** function.
```

install.packages("gmodels")
library(gmodels)
CrossTable(flights$depdelay, flights$arrdelay)
![cross table]({{ '/assets/images/IntroToR_007.png' | relative_url }})
```
 

**Descriptive Statistics**The **summary()** gives a summary of the object. If the object is a data set, it gives a summary of all the variables in a data set and if it is a variable, it gives a summary of the variable. Other descriptions can be obtained using the **fivenum()**, **min()**, **mean()**, **max()**, **var()**, **quantile()** functions.
```

summary(flights$distance)
summary(flights)
mean(flights$distance)
sd(flights$distance)
<img src='{{ '/assets/images/IntroToR_008.png' | relative_url }}' alt='descriptive statistics' title='' width='868' height='255' />
```
The **by()** function can be used to view the average candidate approval rates by another category. For example, below, we can see the average approval rates by income category. 
```

summary(flights$distance[flights$dayofweek==1])
by(flights$distance, flights$dayofweek, summary)
![by function]({{ '/assets/images/IntroToR_009.png' | relative_url }})
```

```

```

### **Graphs**

The following codes can be used to make bar charts, pie charts, boxplots and scatterplots. These are just a few of the many data visualizations you can produce using R. Each example shows you how to add more information to better develop the data visualization, so the below images are made using the last code in the entry. **Bar chart**
```

# Bar chart
dayofweektable <- table(flights$dayofweek)
barplot(dayofweektable)
barplot(dayofweektable, main="Frequency of Flights by Day of the Week",  xlab="Day of Week", ylab="Frequency")
![]({{ '/assets/images/R3.1.png' | relative_url }})
```
 

**Histogram**
```

hist(flights$deptime)
hist(flights$deptime, main="Histogram of Departure Time",  xlab="Departure Time", col="lightblue")
![]({{ '/assets/images/R3.2.png' | relative_url }})
```
 

**Scatterplot**
```

plot(flights$dayofweek, flights$deptime)
plot(flights$dayofweek, flights$deptime, pch=3, cex=3, col="darkred")
![]({{ '/assets/images/R3.3.png' | relative_url }})

```
  

### **New Variables**

To generate a new variable that is a combination of other variables, assign the combination to a new variable name.
```

# Example 1
flights$distancemiles <- flights$distance*0.621
summary(flights$distance)
summary(flights$distancemiles)

```
![New variables example 1]({{ '/assets/images/IntroToR_010.png' | relative_url }})

 

```

# Example 2
flights$instate<-NA
flights$instate[flights$originstate==flights$deststate] <- 1
flights$instate[flights$originstate!=flights$deststate] <- 0
CrossTable(flights$instate)

```
![New variables example 2]({{ '/assets/images/IntroToR_011.png' | relative_url }})

 

```

# Example 3
flights$delay <- ""
flights$delay[flights$depdelay==0 & flights$arrdelay==0] <- "not delayed"
flights$delay[flights$depdelay==1 & flights$arrdelay==0] <- "delayed at departure"
flights$delay[flights$depdelay==0 & flights$arrdelay==1] <- "delayed at arrival"
flights$delay[flights$depdelay==1 & flights$arrdelay==1] <- "delayed at both"
CrossTable(flights$delay)
flights$delay <- factor(flights$delay,
                            levels = c("","not delayed", "delayed at departure", "delayed at arrival", "delayed at both"),
                            ordered=TRUE)
CrossTable(flights$delay

```
<img src='{{ '/assets/images/IntroToR_012.png' | relative_url }}' alt='New variables example 3' title='' width='768' height='541' />

 

**Save()** can be used to save a dataset as a native R .RData data file.
```

save(flights, file="Flights 2020.RData")

```
 

### **Managing Data**

**Subsetting Data**To subset, use the **subset()** function. Example 1departure\<\-subset(flights, select\=c(originstate, origin, deptime, depdelay, deststate))  
dim(departure)  
![managing data example 1]({{ '/assets/images/IntroToR_013.png' | relative_url }})

 

Example 2
```

hawaii<-subset(flights, flights$deststate=="Hawaii" & flights$dayofmonth==1)
dim(hawaii)
![managing data example 2]({{ '/assets/images/IntroToR_014.png' | relative_url }})
```
 **DATA**: [airlinecodes.csv](https://maps.library.utoronto.ca/workshops/R1/airlinecodes.php)

Download the airlines dataset by clicking on the link above or using the url *uoft.me/airlinescsv*. **Merging Data**To combine two datasets, you can use the **merge()** function. 
```

airlinecodes <- read.csv("airlinecodes.csv")
flightsmerged <- merge(airlinecodes, flights, by="carrier")
CrossTable(flightsmerged$airline, flightsmerged$diverted)
![merging data]({{ '/assets/images/IntroToR_015.png' | relative_url }})
```
 

**Converting to Data Frame**A data frame is a dataset. To convert output from a function to a data frame, you can use the **as.data.frame()** function.
```

origin<-as.data.frame(table(flights$origin))
names(origin)<-c("code", "origin")
dest<-as.data.frame(table(flights$dest))
names(dest)<-c("code", "dest")
airports <-merge(origin, dest, by="code", all=TRUE)
str(airports)
![converting data]({{ '/assets/images/IntroToR_016.png' | relative_url }})

```
 

**Exporting Data**To export a dataset to a CSV file, you can use the **write.csv()** function.
```

write.csv(airports, file="Airports.csv", row.names=FALSE)
```
 **Resources**\[1] The flights dataset is modified from the [original version](https://www.kaggle.com/divyansh22/flight-delay-prediction) on the Kraggle website.  
\[2] The tutorial code and the workshop Powerpoint presentation can be downloaded from [here](https://maps-library-utoronto-ca.myaccess.library.utoronto.ca/workshops/R1/tutorial.zip).  
\[3] You can enroll in the introductory R Quercus course [here](https://q.utoronto.ca/enroll/ET679B).

 [R Guide (08\.22\.2016\).pdf](/sites/default/public/R%20Guide%20%2808.22.2016%29.pdf)Technique: [Converting data formats](/technique/converting-data-formats), [Cleaning data](/technique/cleaning-data), [Extracting data](/technique/extracting-data) \| Tools: [R](/tools/r-0) \| Data Format: [Statistics](/data-format/statistics)**Date Created:** 2016\-08\-17**Updated:** 2023\-07\-20
