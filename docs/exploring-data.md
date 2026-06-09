---
title: Exploring Data
layout: home
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
created_date: 2016-08-17
nav_order: 2
parent: Introduction to R
---
## Exploring Data

Unless you opened the .csv file beforehand, you don’t know much about the information you just loaded into R. To find out more, use the **dim()** function to find out the dimension of a data set. To view to contents of a dataset, use the **str()**function. The **head()** function displays the first six rows of the dataset and **tail()** displays the last six rows.
```
str(shelters)
```

<img src='/assets/images/1_5.png' alt='List of shelters dataset data columns with the data type and the first few values.' title='' width='839' height='461' />

```
head(shelters)
```
<img src='/assets/images/2_4.png' alt='First six rows of the shelters dataset.' title='' width='861' height='129' />

```
tail(shelters)
```
 <img src='/assets/images/3_4.png' alt='Last six rows of the shelters dataset.' title='' width='812' height='141' />

To open or, in R terminology, print the content of a data set or a variable in the R\-console, simply write the data set or the variable. A data set has 2 dimensions. The first dimension is the row number and the second dimension is the column number. The two dimensions are separated by a comma. For example, shelters\[1,7] prints the value in the first row and seventh column of the shelters dataset, shelters\[1, ] prints the first row and shelters\[,7] prints the seventh column. As you may notice, we use square brackets when isolating data and round brackets when working with functions. To print a range of rows or a range of columns, indicate the range separated by a colon.
```
shelters[1,4]
shelters[1,"shelter_group"]
shelters[1, 1:4]
shelters[200000:200005,c("shelter_group", "program_name", "service_user_count")]
```
<img src='/assets/images/4_4.png' alt='Using shelters dataframe with square brackets to subset.' title='' width='702' height='267' />    

 When we type a variable by itself, it gives us an error message. To access a variable, use the dollar sign “$”. For example, shelters$shelter\_group returns the shelter\_group variable.
```
shelter_group
shelters$shelter_group
```
<img src='/assets/images/5_4.png' alt='Error message when running a column name by itself.' title='' width='555' height='116' />
<img src='/assets/images/6_3.png' alt='Using a variable with the dataset name and the dollar sign.' title='' width='826' height='416' />

### Frequency Tables
The **table()** function can be used to make a frequency table. You will also find functions from external packages that can be used to make frequency tables.
```
table(shelters$program_area)
table(shelters$program_area, useNA = "ifany")
```
<img src='/assets/images/7_2.png' alt='Frequency table of program area variable.' title='' width='358' height='570' />

You can use the **CrossTable()** function from the gmodels package to make a two\-way frequency table. First, you need to install the gmodels package using the **install.packages()** function and load it using the **library()** function.
```
install.packages("gmodels")
library(gmodels)
CrossTable(shelters$program_area, shelters$year
```
 <img src='/assets/images/8_0.png' alt='Crosstabulation of program area by year. ' title='' width='845' height='659' />

### Descriptive Statistics
The **summary()** gives a summary of the object. If the object is a data set, it gives a summary of all the variables in a data set and if it is a variable, it gives a summary of the variable. Other descriptions can be obtained using the **fivenum()**, **min()**, **mean()**, **max()**, **var()**, **quantile()** functions.
```
summary(shelters)
summary(shelters$service_user_count)
mean(shelters$service_user_count, na.rm=TRUE)
sd(shelters$service_user_count, na.rm=TRUE)
```

<img src='/assets/images/9.png' alt='summary statistics of service user count variable using summary, mean, and sd functions.' title='' width='443' height='140' />

The **by()** function can be used to view the average shelter user count rates by another category. For example, below, we can see the average user count by year. 
```
summary(shelters$service_user_count[shelters$year==2026])
```
<img src='/assets/images/10_0.png' alt='Summary statistics of service user count for year 2026.' title='' width='536' height='63' />
```
by(shelters$service_user_count, shelters$year, summary)
```
<img src='/assets/images/11_0.png' alt='Summary statistics of service user count by year.' title='' width='580' height='569' />

```
# Service_user_count grouped by organization
by(shelters$service_user_count, shelters$organization_name, summary)
# Alternative Approach to by()
aggregate(service_user_count ~ organization_name, data=shelters, summary)
```

**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data) \| **Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R) \| **Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)