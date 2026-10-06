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
nav_order: 3
parent: Introduction to R
---
## Exploring Data

### Data overview

Often, the first step after importing a dataset is to get an idea of the structure and the contents of a dataset. The following functions give you an overview of the dataset. 

Use **dim()** to see the number of rows and columns.
```
dim(cchs)
```
<img src='/assets/images/3_1.png' alt='Dimensions of the cchs dataset.' title='' width='839' height='461' />

To view the structure of a dataset, use the **str()** function. 
```
str(cchs)
```
<img src='/assets/images/3_2.png' alt='List of cchs dataset columns with the data type and the first few values.' title='' width='839' height='461' />

The **head()** function displays the first six rows of the dataset and **tail()** displays the last six rows.
```
head(cchs)
```
<img src='/assets/images/3_3.png' alt='First six rows of the cchs dataset.' title='' width='861' height='129' />

```
tail(cchs)
```
<img src='/assets/images/3_4.png' alt='Last six rows of the cchs dataset.' title='' width='812' height='141' />

The **names()** function lists the column headings or the variable names. This can be useful if you want to modify the variable names to make them easier to understand or shorter. 
```
names(cchs)
```
<img src='/assets/images/3_5.png' alt='List of cchs dataset column names.' title='' width='812' height='141' />

### Displaying rows & columns: square brackets

To display or, in R terminology, print the content of a dataset or a variable, type the dataset or the variable. A dataset has 2 dimensions. The first dimension is the row number and the second dimension is the column number. The two dimensions are separated by a comma. For example, **cchs\[1,3]** prints the value in the first row and third column of the cchs dataset. To display a range of rows or a range of columns, use a colon. To display a list of variables, use **c()**.

Note: Square brackets are used to display selections of data, whereas round brackets are used when working with functions.

```
cchs[1, 3]
cchs[1, "age_group"]
cchs[1, 1:3]
cchs[60000:60005, c("health", "mental_health", "activity")]
```
<img src='/assets/images/3_6.png' alt='Selecting rows and columns of the cchs dataset with square brackets.' title='' width='702' height='267' />    


### Variable: incorrect vs correct approach

When we type a variable by itself, it gives us an error message. To access a variable, use the dollar sign “$”. For example, **cchs$mental\_health** returns the **mental\_health** variable.
```
mental_health
cchs$mental_health
```
<img src='/assets/images/3_7.png' alt='Error message when running a column name by itself. Using a variable with the dataset name and the dollar sign correctly. ' title='' width='555' height='116' />



### Frequency tables

The **table()** function can be used to make a frequency table. You will also find functions from external packages that can be used to make frequency tables.
```
table(cchs$mental_health)
table(cchs$mental_health, useNA = "ifany")
```
<img src='/assets/images/3_8.png' alt='Frequency table of mental health.' title='' width='358' height='570' />

You can use the **CrossTable()** function from the gmodels package to make one-way and two\-way frequency tables. First, you need to install the gmodels package using the **install.packages()** function and load it using the **library()** function. By default, **CrossTable()** leaves out missing values. 

```
install.packages("gmodels")
library(gmodels)
CrossTable(cchs$mental_health)
```
<img src='/assets/images/3_9.png' alt='One-way CrossTable of mental health.' title='' width='845' height='659' />


```
CrossTable(cchs$mental_health, cchs$income_quintile)
```
<img src='/assets/images/3_10.png' alt='Crosstabulation of mental health by income quintile.' title='' width='845' height='659' />


### Missing data

The **is.na()** function is used to identify missing values. It gives the results TRUE or FALSE. To get the total number of missing values in a column, we can use the **sum()** function on the **is.na()** function. Similarly, to get the total number of non-missing values, we can add an exclamation mark before **is.na()** to indicate NOT MISSING. 

```
is.na(cchs$mental_health)
```
<img src='/assets/images/3_11.png' alt='TRUE and FALSE values showing missing mental health responses.' title='' width='845' height='659' />

```
sum(is.na(cchs$mental_health))
sum(!is.na(cchs$mental_health))
```
<img src='/assets/images/3_12.png' alt='Counts of missing and non-missing mental health responses.' title='' width='845' height='659' />



### Summary statistics

The **summary()** function gives a summary of an object. If the object is a dataset, it gives a summary of all the variables in a dataset and if it is a variable, it gives a summary of the variable. To calculate the mean and the standard deviation specifically, use the **mean()** and **sd()** functions. **mean()** and **sd()** need `na.rm = TRUE` to ignore missing values.

```
summary(cchs$life_sat)
mean(cchs$life_sat, na.rm = TRUE)
sd(cchs$life_sat, na.rm = TRUE)
```
<img src='/assets/images/3_13.png' alt='Summary statistics of life satisfaction using summary, mean, and sd.' title='' width='443' height='140' />

Additional functions that can give specific summary statistics are **fivenum()**, **min()**, **mean()**, **max()**, **var()**, **quantile()**. 

To obtain the summary statistics of life satisfaction scores for a subset of the dataset, we can enter the subset condition in square brackets in front of the variable. For example, the following code gives the summary statistics of life satisfaction scores for Ontario respondents only. 

```
summary(cchs$life_sat[cchs$province == "ON"])
```
<img src='/assets/images/3_14.png' alt='Summary statistics of life satisfaction for Ontario.' title='' width='536' height='63' />


### Grouped summary statistics

The **by()** function can be used to view summary statistics of life satisfaction by province or by food security category. 

```
# life_sat grouped by province
by(cchs$life_sat, cchs$province, summary)
```
<img src='/assets/images/3_15.png' alt='Summary statistics of life satisfaction by province.' title='' width='580' height='569' />


```
# life_sat grouped by food_security
by(cchs$life_sat, cchs$food_security, summary)
```
<img src='/assets/images/3_16.png' alt='Summary statistics of life satisfaction by food security.' title='' width='580' height='569' />


**aggregate()** gives the same summaries in one compact table.

```
# Alternative approach to by()
aggregate(life_sat ~ food_security, data = cchs, summary)
```
<img src='/assets/images/3_17.png' alt='Summary statistics of life satisfaction by food security using aggregate.' title='' width='845' height='659' />



**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data) \
**Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R) \
**Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)