---
title       : Biostats and Epidemiology
subtitle    : Review for USMLE Step 1
author      : Austin Meyer
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---
<style>
em {
  font-style: italic
}
</style>
<style>
strong {
  font-weight: bold;
}
</style>

## Roadmap

 - Biostatistics - 20 minutes
  - Accuracy versus Precision - 2 minutes
  - Statistical Inference - 3 minutes
  - Distributions - 5 minutes
  - Hypothesis Testing - 10 minutes
 - Epidemiology - 40 minutes
  - Types of Prevention - 2 minutes
  - Types of Outbreaks - 2 minutes
  - Measures of Morbidity and Mortality - 5 minutes
  - Validity and Reliability of Clinical Tests - 6 minutes
  - Measures of Risk - 10
  - Epidemiological Biases - 5 minutes
  - Types of Studies - 10 minutes

--- &vcenter

<div class="centered"><font size="7">Biostatistics</font size></div>

--- &vcenter

## Accuracy is closeness and Precision is repeatability

<div class="centered"><img src='{{page.url.assets}}/img/precision_accuracy.png' width='80%' /></div>

--- &vcenter

## Use these terms to describe levels of belief

 > - Generalizability
  - How applicable is result to general population
 <br><br><br>
 > - P-value
  - Probability of finding a value this extreme by random chance
 <br><br><br>
 > - Confidence Interval
  - Interval over which real population number is found with a specified probability

--- &vcenter

<div class="centered"><font size="7">Ways to describe distributions of data</font size></div>

--- &twocolumn

## Statistical distributions have invariant properties

***=left
![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1-1.png)

***=right
![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-1.png)

--- &twocolumn

## Real distributions can have one or multiple peaks

***=left
![plot of chunk unnamed-chunk-3](assets/fig/unnamed-chunk-3-1.png)


***=right
![plot of chunk unnamed-chunk-4](assets/fig/unnamed-chunk-4-1.png)

--- &twocolumn

## Skew describes the direction of the tail

***=left
![plot of chunk unnamed-chunk-5](assets/fig/unnamed-chunk-5-1.png)


***=right
![plot of chunk unnamed-chunk-6](assets/fig/unnamed-chunk-6-1.png)

--- &twocolumn

## Question

***=left
![plot of chunk unnamed-chunk-7](assets/fig/unnamed-chunk-7-1.png)

***=right
- Which of the following corresponds to the measures of central tendency on the graph?  
 - A. 1: mean, 2: median,  3: mode  
 - B. 2: mean, 1: median,  3: mode  
 - C. 2: mean, 3: median,  1: mode  
 - D. 3: mean, 2: median,  1: mode  
 - E. 3: mean, 1: median,  2: mode  

--- &twocolumn

## Question

***=left
![plot of chunk unnamed-chunk-8](assets/fig/unnamed-chunk-8-1.png)

***=right
- Which of the following corresponds to the measures of central tendency on the graph?  
 - A. 1: mean, 2: median,  3: mode  
 - B. 2: mean, 1: median,  3: mode  
 - C. 2: mean, 3: median,  1: mode  
 - **_D. 3: mean, 2: median,  1: mode_**  
 - E. 3: mean, 1: median,  2: mode  

--- &vcenter

<div class="centered"><font size="7">Understanding hypothesis testing</font size></div>

--- &vcenter

## The null hypothesis (\(H_0\)) is always the default

 > - Assuming there are two or more groups being compared...
 <br><br><br>
 > - \(H_0\): There is no difference in the means of the groups.
 <br><br><br>
 > - For Step 1, probably safe to assume null is always rejected with \(p < 0.05\).
 <br><br><br>
 > - \(H_A\): The difference between the means of the groups is real.

--- &vcenter

## T-test compares measurements from two groups

![plot of chunk unnamed-chunk-9](assets/fig/unnamed-chunk-9-1.png)
 > \(H_0\): There is no difference between the control and disease groups 

--- &vcenter

<div class="centered"><font size="7">Will this be significant?</font size></div>

---

## T-test compares measurements from two groups

 - \(H_0\): There is no difference between the control and disease groups 
 
 - Run the t-test
  
  ```r
  norm1 <- rnorm(5000, mean = 4.75, sd = 1.2)
  norm2 <- rnorm(5000, mean = 5.25, sd = 1.2)
  (t.test(norm1, norm2))$p.value
  ```
  
  ```
  ## [1] 1.506568e-103
  ```
  
  > - Have we rejected the null hypothesis?
  
  > - Yes, we have accepted \(H_A\). There is a difference between control and disease.

--- &vcenter

<div class="centered"><font size="7">Epidemiology</font size></div>

---
