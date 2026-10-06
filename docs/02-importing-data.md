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
nav_order: 2
parent: Introduction to R
---
## Importing Data

### Working directory

The working directory is the location on your computer that R uses as its default folder for saving files and locating existing files. There are two ways to find and set your working directory. 

First, you can use **getwd()** to display the current working directory and **setwd()** to change it. Choose a folder to use for this guide and set it as your working directory.

Note: R uses forward slashes (`/`) in file paths. If you copy a path on Windows, replace any backslashes (`\`) with forward slashes (`/`).

```
getwd()
setwd("/path/to/your/folder")   # paste the path to your new working directory
```

The second way to change the working directory is to use the **Files** tab in the bottom right pane. Browse to the folder you want to use as your new working directory, then click **More** or the **gear** icon, and select **Set As Working Directory**. This approach is best if you do not know the exact path of your new working directory because it lets you browse through the folders on your computer. 

The **dir()** function lists the files and folders in the working directory. It is a quick way to check that your data files are in the right place.

```
dir()
```

### Importing the data

**CSV DATA**: [cchs.csv](https://raw.githubusercontent.com/MDLutoronto/r-intro/main/docs/assets/data/cchs.csv) (**right-click and save**)\
**RDS DATA**: [cchs.rds](https://raw.githubusercontent.com/MDLutoronto/r-intro/main/docs/assets/data/cchs.rds)


Download the CCHS datasets using the links above and save them in the folder you chose as your new working directory.

Use **read.csv()** to import CSV files. Enter the file name in quotation marks inside the parentheses. The dataset is imported and stored as a data object in the R environment. In this guide, we name this data object **cchs_csv**, but you can choose another name. Object names cannot contain spaces and must start with a letter.

```
# Import CSV File
cchs_csv <- read.csv("cchs.csv")
```

RDS is a native R data file format. Use **readRDS()** to import an RDS file. In this guide, we store the RDS data as **cchs** and use it for the rest of the examples.

```
# Import RDS File (R Data Object)
cchs <- readRDS("cchs.rds")
```

 
**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data)\
**Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R)\
**Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)