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
nav_order: 4
parent: Introduction to R
---
## Graphs

The following code examples can be used to create bar charts, histograms, and scatterplots. These are just a few of the many graphs that can be produced using R. Each example demonstrates how additional elements and information can be added to enhance the data visualization. The images shown below were created using the final version of the code in each example.

### Bar chart

```
# Bar chart
stress_table <- table(cchs$stress)
barplot(stress_table)
barplot(stress_table, 
        main = "Stress Levels in the 2022 CCHS",  
        ylab = "Frequency",
        xlab = "Stress Level")
```
<img src="{{ '/assets/images/barchart.png' | relative_url }}  alt='Barchart of stress levels.' title='Stress Levels in the 2022 CCHS' width='633' height='463' />


### Histogram

```
# Histogram
hist(cchs$life_sat)
hist(cchs$life_sat, breaks = seq(-0.5, 10.5, by = 1))
hist(cchs$life_sat, 
     breaks = seq(-0.5, 10.5, by = 1),
     main = "Life Satisfaction",  
     xlab = "Life Satisfaction Score", 
     col = "lightblue")
```
<img src="{{ '/assets/images/histogram.png' | relative_url }}  alt='Histogram of life satisfaction score.' title='Life Satisfaction' width='650' height='475' />



### Scatterplot

```
# Scatterplot
plot(cchs$sleep_hours, cchs$life_sat)
plot(jitter(cchs$sleep_hours), jitter(cchs$life_sat))
plot(jitter(cchs$sleep_hours), jitter(cchs$life_sat), pch = 3, cex = 0.7, col = "darkred")
plot(jitter(cchs$sleep_hours), jitter(cchs$life_sat), pch = 3, cex = 0.7, col = cchs$sex)
plot(jitter(cchs$sleep_hours), jitter(cchs$life_sat), 
     pch = 3, cex = 0.7, col = cchs$sex,
     main = "Sleep Hours and Life Satisfaction by Sex",
     ylab = "Life Satisfaction Score", 
     xlab = "Sleep Hours")

# Add legend
legend("bottomright", legend = levels(cchs$sex), col = 1:2, pch = 3)
```

<img src="{{ '/assets/images/scatterplot.png' | relative_url }}  alt='Scatterplot of sleep hours and life satisfaction colour coded by sex.' title='Sleep Hours and Life Satisfaction by Sex' width='643' height='470' />



**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data)\
**Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R)\
**Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)