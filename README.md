![Logo](https://download.logo.wine/logo/R_(programming_language)/R_(programming_language)-Logo.wine.png)


#  R-programming (i only have 10 days to learn it all) Day 2 today, could'nt make a Repo before, so here it goes....
Learn R with me :)
#  Introduction
R is a programming language for statistical analysis and visualization. Using R, you can take raw data and understand the trends and patterns in it. You can also use R to create customizable, professional-looking visualizations.This document embarks a journey of mine which anyone can be a part of by clicking the fork button.


## Installation

```bash
Installing R on Windows OS
1. To install R on Windows OS:
2. Go to the CRAN website. (https://cran.r-project.org/)
3. Click on "Download R for Windows".
4. Click on "install R for the first time" link to download the R executable (.exe) file.
5. Run the R executable file to start installation, and allow the app to make changes to your device.
6. Select the installation language.
7. Follow the installation instructions.
8. Click on "Finish" to exit the installation setup.
9. R has now been sucessfully installed on your Windows OS. Open the R GUI to start writing R codes.


Installing R on MacOS X
Installing R on MacOS X is very similar to installing R on Window OS. The difference is the file format that you have to download. The procedure is as follows:

1. Go to the CRAN website.
2. Click on "Download R for macOS".
3. Download the latest version of the R GUI under (.pkg file) under "Latest release". 
4. You can download much older versions by following the "old directory" or "CRAN archive" links.
5. Run the .pkg file, and follow the installation instructions.
```

# Getting started
Some basic vocabulary and concepts we'll use later on. If you already have some programming experience, you can probably skim this section.

# Functions and Arguments
There are plenty of helpful built-in functions in R used for various purposes. Some of the most popular ones are:

1. min(), max(), mean(), median() – return the minimum / maximum / mean / median value of a numeric vector, correspondingly
2. sum() – returns the sum of a numeric vector
3. range() – returns the minimum and maximum values of a numeric vector
4. abs() – returns the absulute value of a number
5. str() – shows the structure of an R object
6. print() – displays an R object on the console
7. ncol() – returns the number of columns of a matrix or a dataframe
8. length() – returns the number of items in an R object (a vector, a list, etc.)
9. nchar() – returns the number of characters in a character object
10. sort() – sorts a vector in ascending or descending (decreasing=TRUE) order
11. exists() – returns TRUE or FALSE depending on whether or not a variable is defined in the R environment

A function is like a verb; it tells the coumputer to do something. What that "something" is depends on the function. And an argument is information that the function needs in order to run

For example :

```bash
print("Welcome to R!")
```
The function above, tells R to print out whatever was passed to it, the argument is inside the parantheses.

You can think of a functions like verbs, and arugments nouns. Just like verbs, not all functions need arguments ("I smiled"), and some functions need more than one ("I put the flowers in the vase").
