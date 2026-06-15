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
nav_order: 5
parent: Introduction to R
---
## Managing Data

### Subsetting Data
To subset, use the **subset()** function. You can subset by columns, conditions, or both.    
To select a set of columns, you can use the select argument.
```
# Subsetting By Column 
shelterprograms <- subset(shelters, select=c(year, organization_name, shelter_group, program_name))
```
 To subset a dataset by a set of conditions, you can either enter the conditions as a second argument after entering the dataset or use the subset argument.
```
# Subsetting By Condition
youth2024_2026 <- subset(shelters, sector=="Youth" & year>=2024)
```
  
**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data) \| **Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R) \| **Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)