---
title       : Project Documentation 
subtitle    : How to predict car fuel efficiency online
author      : Lingli Peng
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Online Prediction Application

- This application provides a convenient way for people to check the car fuel efficiency online
- It applies prediction based on regression modeling 
- It is coded using rstudio and shiny 

---

## How to Use the Online Application

1. Go to https://linglipeng.shinyapps.io/DataProductProject
2. Input values for both car weight (lb/1000) and number of cylinders
3. The application allows minimum of 1 and maxmum of 6 when inputing car weight
4. The provided input choices for number of cylinders are 4, 6 and 8
5. The predicted car miles per gallon value will be automatically calculated and displayed based on the input values

---

## Dataset mtcars

- mtcars dataset is used to build a regression model for the prediction. It comprises fuel consumption and 10 aspects of automobile design and performance for 32 automobiles


```r
data(mtcars)
str(mtcars)
```

```
## 'data.frame':	32 obs. of  11 variables:
##  $ mpg : num  21 21 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 ...
##  $ cyl : num  6 6 4 6 8 6 8 4 4 6 ...
##  $ disp: num  160 160 108 258 360 ...
##  $ hp  : num  110 110 93 110 175 105 245 62 95 123 ...
##  $ drat: num  3.9 3.9 3.85 3.08 3.15 2.76 3.21 3.69 3.92 3.92 ...
##  $ wt  : num  2.62 2.88 2.32 3.21 3.44 ...
##  $ qsec: num  16.5 17 18.6 19.4 17 ...
##  $ vs  : num  0 0 1 1 0 1 0 1 1 1 ...
##  $ am  : num  1 1 1 0 0 0 0 0 0 0 ...
##  $ gear: num  4 4 4 3 3 3 3 4 4 4 ...
##  $ carb: num  4 4 1 1 2 1 4 2 2 4 ...
```


---

## Prediction Example

- Here is an example of prediction based on regression modeling with the mtcars dataset
- Predictors are weight (wt) and number of cylinders (cyl)
- Response is mileage per gallon (mpg)


```r
data(mtcars)
x1 <- mtcars$wt
x2 <- mtcars$cyl
y <- mtcars$mpg
lm1 <- lm(y ~ x1 + factor(x2))
predict(lm1, newdata = data.frame(x1 = 3, x2 = 6))[[1]]
```

```
## [1] 20.12
```


- The predicted mpg value is 20.12 for a car of 3000 lb and 6 cylinders
