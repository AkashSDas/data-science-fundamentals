# Notes on data analysis

---

## Table of contents

---

1. How to work with missing data
2. Binning
3. How to choose the right visualization method
4. Continuous numerical variable
5. Categorical variable
6. Correlation and causation
7. Residual plot

## How to work with missing data

---

Steps for working with missing data

- Identify the missing data
- Deal with missing data
- Correct missing data

### Deal with missing data

---

How to deal with missing data

1. Drop data
    - Drop the whole row
    - Drop the whole column
2. Replace data
    - Replace it by mean
    - Replace it with frequency
    - Replace it based on other functions

## Binning

---

**Why binning?** Binning is a process of transforming continuous numeric variables into discrete categorical **bins** for grouped analysis.

**Example:** In our data set, "horsepower" is a real-valued variable ranging from 48 to 288, it has 57 unique values. What if we only care about the price difference between cars with high horsepower, medium horsepower, and little horsepower (3 types)? Can we rearrange them into three ‘bins' to simplify analysis? We will use the Pandas method 'cut' to segment the 'horsepower' column into 3 bins

## How to choose the right visualization method?

---

When visualizing individual variables, it is important to first understand what type of variable you are dealing with. This will help us find the right visualization method for that variable.

## Continuous numerical variables

---

Continuous numerical variables are variables that may contain any value within some range. Continuous numerical variables can have the type **int64** or **float64**. A great way to visualize these variables is by using **scatterplots** with fitted lines

In order to start understanding the (linear) relationship between an individual variable and the price. We can do this by using **regplot**, which plots the **scatterplot** plus the fitted regression line for the data.

## Categorical variables

---

These are variables that describe a 'characteristic' of a data unit and are selected from a small group of categories. The categorical variables can have the type "object" or **int64**. A good way to visualize categorical variables is by using **boxplots.**

## Correlation and Causation

---

**Correlation** measures the extent of interdependence between variables.

**Causation is** the relationship between cause and effect between two variables.

It is important to know the difference between these two and that correlation does not imply causation. Determining correlation is much simpler the determining causation as causation may require independent experimentation.

### Pearson Correlation

---

The Pearson Correlation measures the linear dependence between two variables X and Y. The resulting coefficient is a value between -1 and 1 inclusive, where:

- 1 - Total positive linear correlation
- 0 - No linear correlation, the two variables most likely do not affect each other
- -1 - Total negative linear correlation

### P-value

---

What is this P-value? The P-value is the probability value that the correlation between these two variables is statistically significant. Normally, we choose a **significance level of 0.05**, which means that we are 95% confident that the correlation between the variables is significant.

By convention, when the

- the p-value is < 0.001, we say there is strong evidence that the correlation is significant.
- the p-value is < 0.05, there is moderate evidence that the correlation is significant
- the p-value is < 0.1, there is weak evidence that the correlation is significant
- the p-value is > 0.1, there is no evidence that the correlation is significant.

### Annova (Analysis of variance)

---

The Analysis of Variance (ANOVA) is a statistical method used to test whether there are significant **differences between the means of two or more groups**. ANOVA returns two parameters:

- **F-test score:** ANOVA assumes the means of all groups are the same, calculates how much the actual means deviate from the assumption, and reports it as the F-test score. A larger score means there is a larger difference between the means.
- **P-value** tells how statistically significant is our calculated score value.

If our price variable is strongly correlated with the variable we are analyzing, expect ANOVA to return a sizeable F-test score and a small p-value.

## Residual Plot

---

A good way to visualize the **variance of the data** is to use a **residual plot**.

**What is a residual?** The difference between the observed value (y) and the predicted value (Yhat) is called the residual (e). When we look at a regression plot, the residual is the distance from the data point to the fitted regression line.

**So what is a residual plot?** A residual plot is a graph that shows the residuals on the vertical y-axis and the independent variable on the horizontal x-axis

**What do we pay attention to when looking at a residual plot?** We look at the spread of the residuals: If the points in a residual plot are randomly spread out around the x-axis then a linear model will be appropriate for the data. Why is that? **Randomly spread out residuals means that the variance is constant, and thus the linear model is a good fit for this data**