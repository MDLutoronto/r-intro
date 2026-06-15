---
title: Importing Data
layout: home
staff:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
maintainer:
    - name: Nadia Muhe
      link: https://library.utoronto.ca/staff/nadia-muhe
created_date: 2016-08-17
nav_order: 1
parent: Introduction to R
---
## Importing Data

### Working directory  
The directory is the place on your computer that is the home for R; therefore, this is where R is saving files and also where R is looking for files. Because R might be using a folder buried deep in your computer’s hard drive, there are two ways of finding and setting your working directory. First, you can use **getwd()** to find the current directory and **setwd()** to set the directory to a different path. NOTE: need to use the forward (/) instead of the backward slash (\\) for directory paths in R.
```
getwd()
setwd("/Users/nadia/Desktop")
```
 The second way is by going under **File** on the menu bar and going down to **Change dir**. This way is best if you do not know the exact name and location of where you want to set your new working directory because it allows you to go through all of the files on your computer. 
 
### Importing Data    
 **DATA**: [shelters.csv](https://maps.library.utoronto.ca/workshops/R1/shelters.php)

Download the shelters dataset by clicking on the link above or using the url *uoft.me/shelterscsv*.     

Use **read.csv()** to read csv files. Set the header option to true if the file has column titles and false otherwise. The default option is always true.
```
shelters<-read.csv("Toronto Daily Shelter Overnight Occupancy 2021-2026.csv")
```
 
**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data) \| **Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R) \| **Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)