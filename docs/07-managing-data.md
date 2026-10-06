---
title: Managing Data
layout: home
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
created_date: 2016-08-17
nav_order: 7
parent: Introduction to R
---
## Managing Data

### Subsetting by variables
To subset, use the **subset()** function. You can subset by variables (columns), observations (rows), or both. The result is saved as a new object, so the original **cchs** dataset stays unchanged.

To select a set of variables, use the `select` argument. Unlike square brackets, variable names inside `select` do not need quotation marks.

```
# Subsetting by Variables (Columns)
lifestyle <- subset(cchs, select = c(id, sleep_hours, activity, fruit_veg, screen_workday, screen_offday))
```

### Subsetting by observations

To subset by observations, enter one or more conditions as the second argument. In this example, we keep respondents aged 18 to 34 who answered both screen time questions (i.e., screen variables are not missing). Since we want all conditions to be true, we combine conditions with **&** (and) operator.

```
# Subsetting by Observations (Rows)
young_adult_screen_complete <- subset(cchs, age_group == "18-34" & !is.na(screen_workday) & !is.na(screen_offday))
```

### Sorting data

The **order()** function is used inside square brackets to sort rows by a variable. By default, rows are sorted from lowest to highest. Add `decreasing = TRUE` to sort from highest to lowest.

```
# Sorting Data
cchs <- cchs[order(cchs$income), ]
cchs <- cchs[order(cchs$income, decreasing = TRUE), ] # highest to lowest
```

**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data)\
**Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R)\
**Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)