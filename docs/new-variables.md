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
nav_order: 4
parent: Introduction to R
---
## New Variables

To generate a new variable that is a combination of other variables, assign the combination to a new variable name.
```
# Example 1: Unavailable Beds Percentage
shelters$unavailable_bed_rate <- 100 * shelters$unavailable_beds / shelters$capacity_funding_bed
summary(shelters$unavailable_bed_rate)
```
<img src='/assets/images/12_0.png' alt='Creating unavailable_bed_rate variable. ' title='' width='810' height='88' />

 
```
# Example 2: Youth Shelter Services Indicator
shelters$youth <- ifelse(shelters$sector=="Youth", 1, 0)
```
<img src='/assets/images/13.png' alt='Creating youth shelter service indicator variable.' title='' width='400' height='84' />

 
```
# Example 3: Youth Emergency and Transitional Shelter Services
shelters$youthprogram <- NA
shelters$youthprogram[shelters$sector=="Youth" & shelters$program_model=="Emergency"] <- "Youth Emergency"
shelters$youthprogram[shelters$sector=="Youth" & shelters$program_model=="Transitional"] <- "Youth Transitional"
shelters$youthprogram[shelters$sector!="Youth" & shelters$program_model=="Emergency"] <- "Non-Youth Emergency"
shelters$youthprogram[shelters$sector!="Youth" & shelters$program_model=="Transitional"] <- "Non-Youth Transitional"
CrossTable(shelters$youthprogram)
```
<img src='/assets/images/14_2.png' alt='Creating youth emergency and transitional shelter service variable. ' title='' width='755' height='373' />

```
# Convert to ordered factor
shelters$youthprogram <- factor(shelters$youthprogram, 
                       levels = c("Youth Emergency", "Youth Transitional", "Non-Youth Emergency", "Non-Youth Transitional"), 
                       ordered = TRUE)
CrossTable(shelters$youthprogram)
```
<img src='/assets/images/15_0.png' alt='Youth emergency and transitional shelter service variable converted to factor.' title='' width='752' height='319' />

 

**save()** can be used to save a dataset as a native R .RData data file.
```
# Saving Data
save(shelters, file="Toronto Shelter Services 2021-2026.RData")
```

```
# Exporting Data As CSV
write.csv(shelters, file="Toronto Shelter Services 2021-2026.csv", row.names=FALSE)
```

**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data) \| **Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R) \| **Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)