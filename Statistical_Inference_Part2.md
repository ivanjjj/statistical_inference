---
title: "Statistical Inference - Inferential Data Analysis"
output:
  html_document:
    keep_md: yes
author: Ivan Jennings
---

## Overview
Analysis of the ToothGrowth data set within the R package. We're going to perform some basic exploratory data analysis as well as using confidence intervals and/or hypothesis tests to compare tooth growth by supp and dose.

## Loading and reviewing data

```r
library(lattice)
data("ToothGrowth")
str(ToothGrowth)
```

```
## 'data.frame':	60 obs. of  3 variables:
##  $ len : num  4.2 11.5 7.3 5.8 6.4 10 11.2 11.2 5.2 7 ...
##  $ supp: Factor w/ 2 levels "OJ","VC": 2 2 2 2 2 2 2 2 2 2 ...
##  $ dose: num  0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 ...
```

We can see that there are 60 observations of three variables, len, supp and dose. Let's also take a look at the summary of the data.


```r
summary(ToothGrowth)
```

```
##       len        supp         dose      
##  Min.   : 4.20   OJ:30   Min.   :0.500  
##  1st Qu.:13.07   VC:30   1st Qu.:0.500  
##  Median :19.25           Median :1.000  
##  Mean   :18.81           Mean   :1.167  
##  3rd Qu.:25.27           3rd Qu.:2.000  
##  Max.   :33.90           Max.   :2.000
```

The summary above along with the documentation of the data set in r using the function ?ToothGrowth gives us an overview of the data that we are looking at. Here's the description from the R documentation:

*"The response is the length of odontoblasts (cells responsible for tooth growth) in 60 guinea pigs. Each animal received one of three dose levels of vitamin C (0.5, 1, and 2 mg/day) by one of two delivery methods, orange juice or ascorbic acid (a form of vitamin C and coded as VC)."*

Here is a plot of the data in a graph for us to get an idea of how the data looks:


```r
xyplot(len ~ supp | factor(dose),
       data = ToothGrowth,
       layout = c(3,1),
       xlab = "Delivery Method",
       ylab = "Length of Odontoblasts",
       labels = c(1,2,3)
       )
```

![](Statistical_Inference_Part2_files/figure-html/unnamed-chunk-3-1.png)<!-- -->

The above plot shows us each dosage (0.5, 1, 2)  and each delivery method (OJ = Orange Juice, VC = Ascorbic Acid)

We can see from the plot that as the dosage increases, the tooth length increases as well. We can also see that for ascorbic acid the effect seems to be lower for 0.5 and 1.0 doses compared to the orange juice delivery method.