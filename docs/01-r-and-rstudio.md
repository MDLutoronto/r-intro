

---
title: RStudio
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
### R and RStudio

This guide helps you get started with the R and RStudio software and R code. You can install R from the [R homepage](https://www.r-project.org/). And you can install RStudio from the [RStudio homepage](https://rstudio.com/). 


## R

R is a programming language and a free software environment to write and execute the R language. The latest version of this free R software environment can be downloaded [here](https://cran.r-project.org/mirrors.html) (mirror: [here](https://cran.utstat.utoronto.ca/)). Select the closest mirror. If you are not sure, select 0-Cloud. Then you will need to select the operating system of your computer whether it is Linux, Mac or Windows. 

The basic R environment looks like this. ![Getting Started with R and RStudio - 1 R Console]({{ '/assets/images/R%26RStudio1_0.png' | relative_url }})

 

The console window is where you type and submit your R commands. The results of your code will also appear in this window. Entered commands appear in **red** and the results of your commands will appear **blue**. 

Instead of typing your code in the console window, you can also enter your code in the R script window. To open a new script window, go the **File** menu and select **New Script**. For clarity, you can organize these windows by going to the **Windows** menu and selecting either **Tile Horizontally** or **Tile Vertically**. 	

![Getting Started with R and RStudio - 2 R Console and Script]({{ '/assets/images/R%26RStudio2_0.png' | relative_url }}) 

Your screen should look like this, with your script editor on one side and the console on the other. Now, you are ready to begin using R! 

**EXECUTING CODE**

R is a code-based program (you have to type what you want it to do rather than clicking buttons).  You can type your code in the console window or in the R script window. If you are writing your code directly in the console window, hit **enter** to submit and run the code.

There are two options to run a line of code from the R script window:
1. Use the shortcut Ctrl + R
2. Go to the **Edit menu** and click on **Execute** (the button is greyed out if you are in the console window).

To run multiple lines of code, select the lines of code and use one of the options above. 


## RStudio

RStudio is an Integrated Development Environment that provides free and open-source tools for R. You can run your data analysis in the basic R environment. However, RStudio does have a more intuitive interface and more tools to help you write your R code. 

You need to install both R and RStudio to use R in RStudio. The latest version of the free RStudio environment can be downloaded [here](https://www.rstudio.com/products/rstudio/download/). The free open-source version is RStudio Desktop. 

The RStudio interface has many windows. You will find the name of each window in the top-left corner of that window. On the left-hand side, you have the console window where you can type and submit R code. The results of your code will also appear in this window. ![Getting Started with R and RStudio - 3 RStudio Interface Console]({{ '/assets/images/R%26RStudio3_1.png' | relative_url }})



You can also type your code in the R script window. To open a new R script file, go to the **File** menu, then go to **New File** and select **R Script**. You can also click on the white page icon on the toolbar to open a new R script page. 

You can interact with RStudio by typing your code in the console window or in the R script page. The advantage of the R script is that you can save your code, edit it later and share it with others. ![Getting Started with R and RStudio - 4 RStudio Interface Script]({{ '/assets/images/R%26RStudio4_0.png' | relative_url }})

 

To submit R code from the console window, simply type your code and hit enter. To submit R code from the R script window, make sure your cursor is on the line of code you want to submit and either click on the Run icon on the toolbar or use the shortcut CTRL-ENTER (CMD-Return for Mac). 

Some additional windows that are useful when you are getting started are the following: the environment window, the files window, the plots window, and the help window. The environment window is your workspace. Any data that you import or create can be found in this window. The files window shows the list of files in your home directory and allows you to change your home directory. The plots window shows you graphs that you create. And finally, the help window allows you to search and view the help file of specific functions. 

To rearrange these windows, go to the **Tools** menu and select **Global Options**. Click on the **Pane Layout** tool from the list on the left-hand side. You can use the Pane Layout tool to rearrange the windows. 

Whenever you start a new data analysis project that you want to work on in RStudio, it is useful to create an RStudio project for it. A project file allows you to pick up where you left off whenever you quit RStudio. To create a new project, go to the **File** menu and select **New Project**. You can associate your new project with a new directory or an existing directory. After you create the project, you will find the project name in the top-right corner of the RStudio interface. The home directory in the files window will also be updated to your project folder and you will find the project file in this folder. 


# Search and Help
??csv
help(read.table)


## Getting Started with R code

The basic format for commands is the combination of functions and argument values. A function is a word or an abbreviation of words, followed by brackets. For example: **read.table()**, **xrange()**, or **plot()**. The words give you a sense of what the function is supposed to do. You enter the necessary information or argument values inside the brackets. For example, inside the parenthesis of the read.table() function, you enter the data table you want to read. Finally, you can use functions on other functions. Here are some examples below. 	

![Getting Started with R and RStudio - 9 sum()]({{ '/assets/images/R%26RStudio9.jpg' | relative_url }}) 

This gives you the sum of 4 and 5. ![Getting Started with R and RStudio - 10 R mean()]({{ '/assets/images/R%26RStudio10.jpg' | relative_url }}) 

This gives you the mean of the sums of the two different sets of numbers, thus combining the sum function and the mean function. Once you know more about R, you can even write your own functions. More on scripting will come later.  

Troubleshooting tips:
  * Commands are case-sensitive, i.e., load() will run and Load() will not
  * Always check spelling – some commands are pluralized and some are not, i.e., names() will run and name() will not
  * Check for spaces and misplaced symbols
  * Check the help file for the function you are using

Useful hotkeys:
  * Save: ‘Ctrl + S’
  * New Script: ‘Ctrl + N’
  * Run line or selection: ‘Ctrl + R’
  * Undo: ‘Ctrl + Z’
  * Clear window: ‘Ctrl + L’

 

### **PACKAGES**

R packages consist of new functions and datasets contributed by the R-users community. The CRAN package repository has more than 18,000 packages. You can search for packages [here](https://cran.r-project.org/web/packages/). There is a large variety of R packages that exist. Some are good for creating graphics; some are good for statistical analysis. Not to worry, you won’t need to download all of them. 

Using packages is a two-step process. First you must install the package you want, and then you must load it into R.
* Using the menu:
	1. Packages -> Install Packages -> Select [package]
	2. Packages -> Load package -> Select [package]
* Using R code:
	1. install.packages(“package”)
	2. library(package)

Troubleshooting tips:
* Check that your desired package is loaded into R from the Packages window
* Packages are built on each other. When installing a new package, it should install the ones it depends on too. If a package is not working, double-check that its dependent packages are also installed.
* Because packages are open source, be sure you check for updates frequently; this does not occur automatically
* When all else fails, there are, usually, comprehensive entries on the CRAN website on each package.

 

### **INTRODUCTORY CODE**

The R environment can be used to make calculations and create variables. As a new R-user, you might want to practice these simple exercises by typing them into the console window.  
![Getting Started with R and RStudio - 5 R calculations and assignment]({{ '/assets/images/R%26RStudio5.jpg' | relative_url }}) 

There are different data types in R. These data types can be numeric, integer, logical/boolean, character/string, vector, matrix, array, list, data-frame etc. It is useful to know the data type in order to know what functions can be performed on the data object. To determine the data type, you can use the **class()** or **mode()** function. The following commands create different variables and check their type using the **class()** function. It is also possible to convert from one data type to another by using functions such as **as.integer()**, **as.vector()**, **as.matrix()** etc.  
![Getting Started with R and RStudio - 6 R Data type]({{ '/assets/images/R%26RStudio6.jpg' | relative_url }}) 

As you can see, pi has been converted from a number to an integer to a vector to a matrix using various R functions. 

Before you take a deep dive into learning R, here are some other basic tips, including some initial steps to take in case you encounter an error.
* Environment: The R environment is current workspace. You can view all of the data objects imported or created in the environment using the **ls()** function.
* Functions: As previously described, functions perform various tasks in R. Each function has a specific number and type of arguments. You can find more information on these arguments in the help file of that function.
* Every time a command is ran there is no way of undoing it. For this reason, you may choose to write your code in the R script window before running it.
* Printing: Print is R jargon for viewing a data object; it gets ‘printed’ in the console window. To print a data object, simply type and run its name. For example if 67 is assigned to blue (“blue<-67”), then blue must be printed to see its assigned value.

![Getting Started with R and RStudio - 7 R "blue"]({{ '/assets/images/R%26RStudio7.jpg' | relative_url }})

 

Here are some operators you may encounter:

| ?? | You can use two questions marks to search for functions associated with a specific topic (eg. ??csv). |
| ? | You can use one question mark to open the help file for a specific function (eg. ?read.csv). |
| # | The number sign is used to enter a comment to describe the following commands. See the example below: |
| $ | The $ sign is used to access one variable or column in a dataset. (eg. dataname$age). |


**Technique:** [Converting data formats](https://mdlutoronto.github.io/tutorials-search/?technique=Converting+data+formats), [Cleaning data](https://mdlutoronto.github.io/tutorials-search/?technique=Cleaning+data), [Extracting data](https://mdlutoronto.github.io/tutorials-search/?technique=Extracting+data) <br> 
**Tools:** [R](https://mdlutoronto.github.io/tutorials-search/?tool=R) <br> 
**Data Format:** [Statistics](https://mdlutoronto.github.io/tutorials-search/?dataFormat=Statistics)