---
title: New Variables
layout: home
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
created_date: 2016-08-17
nav_order: 5
parent: Introduction to R
---
## New Variables

The following examples create three types of variables: a binary variable with values of 0 and 1, a categorical variable that is later converted to a factor, and a count variable calculated as the sum of values across rows.

### Example 1: Binary Variable

```
# Example 1: Binary Variable
# Food Insecurity Indicator
table(cchs$food_security, useNA = "ifany")
cchs$food_insecure <- ifelse(cchs$food_security == "Secure", 0, 1)
# Check
table(cchs$food_security, cchs$food_insecure, useNA = "ifany")
```
<img src="{{ '/assets/images/5_1.png' | relative_url }}  alt='Two-way frequency table of food security variable by food insecure indicator variable.' title='' width='810' height='88' />


### Example 2: Categorical Variable

```
# Example 2: Categorical Variable
# Smoking & Drinking Risk Categories
table(cchs$smoking, useNA = "ifany")
table(cchs$drinking, useNA = "ifany")
```
<img src="{{ '/assets/images/5_2.png' | relative_url }}  alt='Two frequency tables of smoking and drinking.' title='' width='810' height='88' />


```
cchs$risk <- NA
cchs$risk[cchs$smoking == "Current" & cchs$drinking == "Regular"] <- "Both"
cchs$risk[cchs$smoking == "Current" & cchs$drinking != "Regular"] <- "Smoker"
cchs$risk[cchs$smoking != "Current" & cchs$drinking == "Regular"] <- "Drinker"
cchs$risk[cchs$smoking != "Current" & cchs$drinking != "Regular"] <- "Neither"
# Check
table(cchs$smoking, cchs$drinking, useNA = "ifany")
table(cchs$risk, useNA = "ifany")
```
<img src="{{ '/assets/images/5_3.png' | relative_url }}  alt='One two-way frequency table of smoking by drinking. One frequency table of the risk categorical variable.' title='' width='810' height='88' />


```
# Convert from character to factor
str(cchs$risk)
cchs$risk <- factor(cchs$risk, levels = c("Both", "Smoker", "Drinker", "Neither"))
str(cchs$risk)
table(cchs$risk, useNA = "ifany")
```
<img src="{{ '/assets/images/5_4.png' | relative_url }}  alt='Converting the risk character variable into a factor variable.' title='' width='810' height='88' />



### Example 3: Count Variable

```
# Example 3: Count Variable
# Total Chronic Conditions Reported
cchs$chronic_count <- rowSums(cbind(cchs$diabetes, cchs$hbp, cchs$cholesterol, cchs$mood, 
                                cchs$anxiety, cchs$fatigue, cchs$msk, cchs$cardiovascular), 
                      na.rm = TRUE)
# Check
table(cchs$chronic_count, useNA = "ifany")
```

<img src="{{ '/assets/images/5_5.png' | relative_url }}  alt='Frequency variable of the total chronic conditions count variable.' title='' width='752' height='319' />

 
 

**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data)\
**Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R)\
**Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)