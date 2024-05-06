
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

# Reading data 

When loading the data into R, you need to tell it two things, the first is what type of data structure the data is in and the second is where to find the data.

Sure, here's a basic R code that reads a dataset and fits a simple linear regression model to it:

```R
# Load necessary libraries
library(readr)  # for reading data
library(dplyr)  # for data manipulation
library(ggplot2)  # for visualization
library(caret)  # for modeling

# Read the dataset (replace "dataset.csv" with your dataset file name)
data <- read_csv("dataset.csv")

# Explore the structure of the dataset
str(data)

# View the first few rows of the dataset
head(data)

# Check summary statistics of numeric variables
summary(data)

# Plotting the data (replace x_var and y_var with your variables)
ggplot(data, aes(x = x_var, y = y_var)) +
  geom_point() +
  labs(x = "X Variable", y = "Y Variable") +
  ggtitle("Scatter Plot of X vs Y")

# Split data into training and testing sets (70% training, 30% testing)
set.seed(123)  # for reproducibility
trainIndex <- createDataPartition(data$y_var, p = .7, 
                                  list = FALSE, 
                                  times = 1)
data_train <- data[trainIndex,]
data_test <- data[-trainIndex,]

# Fit a linear regression model (replace y_var with your dependent variable)
model <- lm(y_var ~ ., data = data_train)

# Summary of the model
summary(model)

# Make predictions on the test data
predictions <- predict(model, newdata = data_test)

# Evaluate the model (replace actual_y with the actual values from your test data)
accuracy <- sqrt(mean((predictions - data_test$y_var)^2))
print(paste("Root Mean Squared Error:", accuracy))
```

Make sure to replace `"dataset.csv"` with the actual file name of your dataset and `"x_var"` and `"y_var"` with the names of your independent and dependent variables respectively.

This code assumes that your dataset is in a CSV format. If your dataset is in a different format (e.g., Excel), you may need to use different functions (e.g., `read_excel()` from the `readxl` package) to read it.

# Cleaning data

Cleaning the dataset typically involves several steps to ensure that the data is in a suitable format for analysis. Here are some common data cleaning steps you can take in R:

1. **Handling Missing Values**: Check for missing values in the dataset and decide how to handle them. You can either remove rows or columns with missing values, impute missing values with a mean, median, or mode, or use more advanced techniques like predictive imputation.

```R
# Check for missing values
missing_values <- colSums(is.na(data))
print(missing_values)

# Remove rows with missing values
data <- na.omit(data)

# Impute missing values (replace "column_name" with the name of the column)
data$column_name[is.na(data$column_name)] <- mean(data$column_name, na.rm = TRUE)
```

2. **Removing Duplicates**: Check for and remove duplicate rows in the dataset.

```R
# Remove duplicate rows
data <- distinct(data)
```

3. **Handling Outliers**: Identify and deal with outliers in the dataset. This could involve removing them, transforming them, or using robust statistical techniques.

```R
# Identify outliers using boxplots
boxplot(data$numeric_variable)

# Remove outliers (replace "column_name" with the name of the column)
data <- data[!(data$column_name > upper_limit | data$column_name < lower_limit), ]
```

4. **Standardizing or Scaling Variables**: If your dataset contains variables on different scales, you might want to standardize or scale them to have a mean of 0 and a standard deviation of 1.

```R
# Standardize variables (replace "column_name" with the name of the column)
data$column_name <- scale(data$column_name)
```

5. **Converting Data Types**: Ensure that variables are in the correct data type (e.g., numeric, factor, character) for analysis.

```R
# Convert to factor (replace "column_name" with the name of the column)
data$column_name <- as.factor(data$column_name)
```

6. **Renaming Variables**: Rename variables for clarity and consistency.

```R
# Rename variables
names(data)[names(data) == "old_column_name"] <- "new_column_name"
```

These are just some common data cleaning steps. Depending on the specific characteristics of your dataset, you may need to perform additional cleaning steps.

# Graphing data

Here are code snippets demonstrating how to implement some of these commonly used models in R:

1. **Linear Regression**:
```R
# Example using lm() function
lm_model <- lm(dependent_variable ~ independent_variable1 + independent_variable2, data = your_data)
summary(lm_model)
```

2. **Logistic Regression**:
```R
# Example using glm() function
logit_model <- glm(outcome ~ predictor1 + predictor2, family = binomial(link = "logit"), data = your_data)
summary(logit_model)
```

3. **Decision Trees**:
```R
# Example using rpart package
library(rpart)
tree_model <- rpart(target_variable ~ ., data = your_data)
```

4. **Support Vector Machines (SVM)**:
```R
# Example using e1071 package
library(e1071)
svm_model <- svm(target_variable ~ ., data = your_data, kernel = "radial")
```

5. **k-Nearest Neighbors (k-NN)**:
```R
# Example using class package
library(class)
knn_model <- knn(train = train_data, test = test_data, cl = train_labels, k = 5)
```

6. **Naive Bayes**:
```R
# Example using e1071 package
naive_bayes_model <- naiveBayes(target_variable ~ ., data = your_data)
```

7. **Clustering Algorithms (e.g., K-means)**:
```R
# Example using stats package
cluster_model <- kmeans(your_data, centers = 3)
```

8. **Principal Component Analysis (PCA)**:
```R
# Example using stats package
pca_model <- prcomp(your_data, scale = TRUE)
```

9. **Time Series Models (e.g., ARIMA)**:
```R
# Example using forecast package
library(forecast)
arima_model <- auto.arima(your_time_series_data)
```

10. **Neural Networks**:
```R
# Example using neuralnet package
library(neuralnet)
nn_model <- neuralnet(target_variable ~ predictor1 + predictor2, data = your_data, hidden = c(5, 3))
```

These snippets should give you a starting point for implementing these models in R. Remember to replace "your_data" with your actual dataset and variables.

# Some handy tips:
1. If you get an error message you can't figure out, copy the text of the error and Google it to see if anyone else has had the same problem. 99 times out of 100 you'll find that someone else has already come up with a solution!
2. Double-check your capitalization. I find that a good 20% of my errors are because I've mis-capitalized something.
3. Read the documentation! Remember that you can quickly pull up the documentation for a certain function by putting a question mark in front of the function name and then running the command.
4. If you're not sure how to start approaching a problem, start by writing out all the steps you want your code to do in English (or your language of choice). Then turn each step into a separate comment in your code and write the code to do that step underneath it. Not only will it help you organize your thoughts, but your code will also be nicely commented when you're done.
5. Remember that you put the arguments for a function in parentheses (), and you get data from inside an object using square brackets []. someText() is a function, someText[] is an object: if you try to pass arguments to an object you'll get an error.
6. If you're not sure why a data_frame isn't acting the way you expect it to, str() is a good place to start figuring out what an object is behaving in a surprising way. You'd be surprised how often I've found out that what I thought was a data_frame ended up being something else entirely!
7. Remember not to put special characters in names. In general, the only non alpha-numeric character you want to use in a name is a period (.) or underscore (_) between words to make it easier to read. You can find a handy style-guide here. (You don't have to follow a style-guide, but it makes it easier for other people to read your code.)
8. You can keep certain lines of code from running but putting a hashtag/pound sign (#) in front of them to turn them into comments. This is called "commenting out" code, and it can be really helpful if you're trying to figure out which lines are generating which errors.
9. Once you start typing a part of R code, like the name of a variable or a function, you can complete words in your code automatically by pressing the TAB key. If there's more than one valid completion, a list of possible completions will drop down. This is really handy when you want to see all your geom options, for example.
10. Read other people's R code. I've learned a lot of handy tips over the years from seeing how other people do things. On Kaggle, you can find R code by going to the kernels page and filtering for kernels written in R.

# This is the end of documentation, i will be adding some repos that is my own work :)
