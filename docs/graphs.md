---
title: Graphs
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
## Graphs

The following codes can be used to make bar charts, pie charts, boxplots and scatterplots. These are just a few of the many data visualizations you can produce using R. Each example shows you how to add more information to better develop the data visualization, so the below images are made using the last code in the entry. 

### Bar chart
```
# Bar chart
shelterservicebysector <- table(shelters$sector)
barplot(shelterservicebysector, 
       main = "Toronto shelter services by sector (2021–2026)",  
       xlab = "Sector", 
       ylab = "Frequency")
```
<img src='/assets/images/Barplot.png' alt='Barchart of shelter services by sector.' title='' width='633' height='463' />


### Histogram
```
# Histogram
hist(shelters$service_user_count, 
    main = "Shelter service user counts",  
    xlab = "Shelter Service User Count", 
    col = "lightblue")
```

<img src='/assets/images/Histogram.png' alt='Histogram of service user counts.' title='' width='650' height='475' />


### Scatterplot
```
# Scatterplot
plot(shelters$service_user_count, shelters$occupancy_rate)
plot(shelters$service_user_count, shelters$occupancy_rate, pch=3, cex=3, col="darkred")
plot(shelters$service_user_count, shelters$occupancy_rate, 
    pch=3, cex=3, col=as.factor(shelters$capacity_type))  

plot(shelters$service_user_count, shelters$occupancy_rate, 
    pch = 3, cex = 3, 
    col=as.factor(shelters$capacity_type),
    xlab = "Service user count", 
    ylab = "Occupancy rate")  

# Add legend to plots
legend("topleft", legend = c("Bed Based", "Room Based"), col = 1:2, pch = 3)
```
<img src='/assets/images/Scatterplot.png' alt='Scatterplot of service user count by occupancy rate colour coded by bed vs room capacity type. ' title='' width='643' height='470' />

**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data) \| **Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R) \| **Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)