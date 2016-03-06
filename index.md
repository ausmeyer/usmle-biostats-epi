---
title       : Biostats and Epidemiology
subtitle    : Review for USMLE Step 1
author      : Austin Meyer
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax, quiz, bootstrap, interactive] 
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
github:
  user: ausmeyer
  repo: intro-biostats-epi
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
body {
  background-color: #000;
}
</style>

<!-- Limit image width and height -->
<style type="text/css">
img {     
  max-height: 500px;     
  max-width: 900px; 
}
</style>

## Roadmap

 - Biostatistics - 20 minutes
  - Accuracy versus Precision - 2 minutes
  - Statistical Inference - 3 minutes
  - Distributions - 5 minutes
  - Hypothesis Testing - 10 minutes
 - Epidemiology - 40 minutes
  - Types of Prevention and Outbreaks - 4 minutes
  - Measures of Morbidity and Mortality - 5 minutes
  - Validity and Reliability of Clinical Tests - 6 minutes
  - Measures of Risk - 10 minutes
  - Epidemiological Biases - 5 minutes
  - Types of Studies - 10 minutes

--- .segue
## Biostatistics

--- &vcenter
## There are some important random terms

> - Generalizability
  - How applicable is a finding to the general population
<br>
> - P-value
  - Probability of finding a value this extreme by random chance
<br>
> - Confidence Interval
  - Interval over which population value is found with a specified probability (e.g. 95%)
<br>
> - Efficacy
  - Performance of treatment under ideal circumstances
<br>
> - Effectiveness
  - Performance of treatment under real world circumstances

--- &vcenter
## Precision is repeatability, Accuracy is closeness

![](assets/img/precision_accuracy.png)

--- .segue
## Describing Distributions

--- &twocolumn
## Statistical distributions have invariant properties

***=left
![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-1-1.png)

***=right
![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2-1.png)

---  &radio
## Question #1

Investigators are studying prostate specific antigen (PSA) as a predictor for prostate cancer. To make the statistics easier, they are going to assume that PSA is a normally distributed population variable. Which of the following is correct under their assumption?

1. Mode is greater than median
2. Median is greater than mode
3. 95% CI depends on degrees of freedom
4. _Median is equal to mean_
5. Mean is equal to standard deviation

***.hint
The normal distribution is unimodal and symmetric.

***.explanation
The important invariant properties (for you) of normal distributions are the following:

1. Mean = Median = Mode
2. Unimodal
3. Symmetric
4. Area under curve is 1
5. Constant relationship between standard deviation and percentiles

--- &twocolumn
## Real distributions can have one or multiple peaks

***=left
![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png)


***=right
![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4-1.png)

--- &twocolumn
## Skew describes the direction of the tail

***=left
![plot of chunk unnamed-chunk-5](figure/unnamed-chunk-5-1.png)


***=right
![plot of chunk unnamed-chunk-6](figure/unnamed-chunk-6-1.png)

--- &radio2
## Question #2

Which of the following corresponds to the measures of central tendency on the graph from **left to right**? 

1. mean, median, mode
2. mode, mean, median
3. median, mode, mean
4. _mode, median, mean_
5. mean, mode, median

 
***=image
![plot of chunk unnamed-chunk-7](figure/unnamed-chunk-7-1.png)

***.hint
Mode is most common, median is middle, mean is average value.

***.explanation
Always remember that the y-axis on these plots are counts or frequency. Therefore, which line is closest to the peak on the y-axis is the mode. The median is **always** in the middle. The mean is the most susceptible to outliers so in a skewed distribution it will **always** be farthest out on the tail.

--- .segue
## Hypothesis Testing

--- &vcenter
## The null hypothesis (\(H_0\)) is always the default

> - Assume:
  - There are two or more groups being compared, or one group being compared to zero
<br><br><br>
> - \(H_0\): There is no difference in the means of the groups.
<br><br><br>
> - For Step 1, probably safe to assume null is always rejected with \(p < 0.05\).
<br><br><br>
> - \(H_A\): The difference between the means of the groups is real.

--- &twocolumn
## T-test compares means of one or two groups

***=left
![plot of chunk unnamed-chunk-8](figure/unnamed-chunk-8-1.png)

***=right 
<br><br>
> - One sample: \(H_0\) = There is no difference between group mean and zero
<br><br>
> - Two sample: \(H_0\) = There is no difference between the disease and control groups
<br><br>
> - Paired: \(H_0\) = The difference of a measured variable between two time points on the same individuals is zero

--- &vcenter
<div class="centered"><font size="7">Will the plot be significant?</font size></div>

--- &vcenter
## T-test compares means of one or two groups

 - Two sample: \(H_0\) = There is no difference between the disease and control groups
 <br>
 - Run the t-test
  
  ```r
  norm1 <- rnorm(5000, mean = 4.75, sd = 1.2)
  norm2 <- rnorm(5000, mean = 5.25, sd = 1.2)
  (t.test(norm1, norm2))$p.value
  ```
  
  ```
  ## [1] 3.780512e-92
  ```
  > - Have we rejected the null hypothesis?
  <br>
  > - Yes, we have accepted \(H_A\). There is a difference between control and disease.

--- &vcenter
## Chi-squared test uses categorical (count) data

> - Two common tests
 - Test of independence
 - Goodness-of-fit
> - Test of independence
 - \(H_0\): There is no association between the variables under study
 - \(H_A\): There is an association between the variables under study
> - Goodness-of-fit
 - \(H_0\): The number of cases occuring is equal to that expected by chance
 - \(H_A\): The number of cases occuring is unequal to that expected by chance

--- &vcenter
## Always expect a contingency table for chi-squared

|             | Healthy  | Disease  | Total  |
|-------------|---------:|---------:|-------:|
| Exposed     |     40   |     60   |   100  |   
| Not Exposed |    500   |    400   |   900  |   
| Total       |    540   |    460   |  1000  |   
Table 1: A 2x2 contingency table


| Exposure Status | Never Sick  |  Sometimes Sick | Mostly Sick  | Total  |
|-----------------|------------:|----------------:|-------------:|-------:|
| High            |      10     |     20          |   180        |  210   |
| Medium          |      20     |    100          |    20        |  140   |
| Low             |     100     |     40          |    10        |  150   |  
| Total           |     130     |    160          |   210        |  500   |
Table 2: A 3x3 contingency table

--- &vcenter
## The contingency table can be of any size

| Exposure Status | Never Sick  |  Infrequently Sick |  Sometimes Sick |  Mostly Sick |  Always Sick |  Total |
|-----------------|------------:|-------------------:|----------------:|-------------:|-------------:|-------:|
| Super High      |     10      |          90        |       34        |      12      |    12        |   158  |
| Very High       |     30      |         345        |       54        |      43      |    21        |   493  |
| High            |     70      |          57        |       67        |      65      |    32        |   291  |
| Medium          |    200      |          33        |       87        |      25      |    42        |   387  |
| Low             |    130      |          89        |       58        |      45      |    56        |   378  | 
| Very Low        |    100      |          54        |       36        |      23      |    78        |   291  |
| Super Low       |     90      |          23        |       36        |      63      |     8        |   220  |
| Total           |    530      |         691        |      372        |     276      |   249        |  2118  |
Table 3: A 7x5 contingency table

--- &vcenter
## Pearson correlation compares two variables
The correlation can be positive or negative

![plot of chunk unnamed-chunk-10](figure/unnamed-chunk-10-1.png)

--- &twocolumn
## For correlation, r is the critical statistic
***=left
<br>
> - Must be quantitative data
 - **Not count data**
<br><br>
> - \(r =\) correlation between variables
<br><br>
> - \(r^2 = \) amount of variance in y that is explained by x
<br><br>
> - p-value is still used for significance
 - For Step 1, most likely significant at \(p < 0.05\)

***=right
![plot of chunk unnamed-chunk-11](figure/unnamed-chunk-11-1.png)

--- &twocolumn
## A wider spread in \(y\) means a lower \(r^2\)

***=left
![plot of chunk unnamed-chunk-12](figure/unnamed-chunk-12-1.png)

***=right
![plot of chunk unnamed-chunk-13](figure/unnamed-chunk-13-1.png)

--- &radio2
## Question #3

A study was conducted to assess the association between oral contraceptive (OCP) use and confirmed blood clots. The data from the study are presented to the left. Which of the following is the best method to assess the association between OCP use and blood clots?

1. Two sample T-test
2. Analysis of variance
3. Pearson correlation
4. _Chi-square test_
5. Spearman correlation

***=image
|             |   Clot   | No Clot  | Total  |
|-------------|----------|----------|--------|
| OCP Use     |    500   |    400   |   900  |   
| No OCP Use  |     80   |     20   |   100  |   
| Total       |    580   |    420   |  1000  |   

***.hint
What kind of data is this?

***.explanation
The only test available that utilizes categorical data is the Chi-square test. All of the other tests require at least rank or quantitative data.

---  &radio
## Question #4

Investigators developed a new serum biomarker as a predictor for prostate cancer. To test it, they plan a cross-sectional study comprised of two groups. In one group, the researchers will include measurements of men with biopsy confirmed prostate cancer. In the other group, researchers will measure the level of their biomarker in men that have never previously been diagnosed with prostate cancer nor had a positive PSA test. The investigators will assume their biomarker is normally distributed. What is the best test to investigate whether the biomarker can distinguish the two groups?

1. Two sample Mann-Whitney U-test
2. Pearson correlation
3. _Two sample T-test_
4. Chi-squared test
5. Analysis of variance

***.hint
The number of groups and distribution is all that matters

***.explanation
The two sample T-test is the appropriate test in this case. The two sample Mann-Whitney U-test could work as well, but is slightly less efficient for normally distributed data than the T-test. The Pearson correlation requires two measured variables on the same sample. A chi-squared test requires categorical (i.e. count) data. An analysis of variance is typically used to measure the difference in means of three or more groups.

--- &twocolumn
## Hypothesis testing has four possible outcomes

***=left
![](assets/img/truth_table.png)

***=right
<br>
> - Correct - Reject a false \(H_0\)
 - Probability of success is called "power"
 - Power depends on sample size
 - bigger sample = bigger power
> - Correct - Fail to reject a true \(H_0\)
 - Probability determined by \(\alpha\) as \(1-\alpha\)
<br><br>
> - Type 1 - Incorrect rejection of a true \(H_0\)
 - False Positive
> - Type 2 - Failure to reject a false \(H_0\)
 - False Negative

--- .segue
## Epidemiology

--- &vcenter
## Types of prevention
  
> - Primary - __Prevention__
  - An action taken to prevent development of disease in a person who is well
  <br>
> - Secondary - __Screening__
  - Identifying people in whom disease has begun but who do not have signs or symptoms
  <br>
> - Tertiary - __Treatment__
  - Preventing complications in those who have developed signs and symptoms and have been diagnosed
  <br>
> - Quaternary - __Quit overtesting and overtreating__
  - Recent effort to minimize excessive healthcare interventions in disease process

--- &vcenter
## Endemic vs Sporadic vs Epidemic vs Pandemic

![](assets/img/epidemic.jpg)

--- &vcenter
## Metric differences lie in setting and time frame
  
> - Attack rate
  - Typically used during epidemics
  - Number of people who get disease / Number of people who are exposed

> - Incidence
  - Given a __defined period of time__
  - Number of people with disease / Number of people who are exposed

> - Prevalence
  - __No time frame__
  - Number of people with disease/Number of people who are exposed
  - For steady-state, simple diseases (e.g. SIR infections)
    - Prevalence = Incidence x Average Disease Duration

--- &vcenter
## Tests are usually cutoffs on a continuous variable
  
![plot of chunk unnamed-chunk-14](figure/unnamed-chunk-14-1.png)

--- &vcenter
## Sensitivity is true positives / number with disease
  
![plot of chunk unnamed-chunk-15](figure/unnamed-chunk-15-1.png)

--- &vcenter
## Specificity is true negatives / number w/o disease
  
![plot of chunk unnamed-chunk-16](figure/unnamed-chunk-16-1.png)

--- &twocolumn
## PPV and NPV vary based on pre-test probability
  
***=left
![plot of chunk unnamed-chunk-17](figure/unnamed-chunk-17-1.png)

***=right
> - Positive Predictive Value
  - Chance that person has the disease after a positive test result
  - \(PPV = TP / (TP + FP)\)
<br><br>
> - Negative Predictive Value
  - Chance that person does not have disease after a negative test result
  - \(NPV = TN / (TN + FN)\)
<br>  
> - __Both depend on how prevalent the disease is in the population__

--- &radio2
## Question #5

Assume a steady-state population that is not changing in anyway. Which of the following statements is true for people who test positive regarding moving the cutoff for a positive test from the solid to the dotted line?

1. Decrease in test specificity
2. Increase in test sensitivity
3. _Increase in PPV_
4. Increase in NPV
5. Decrease in NPV

***=image
![plot of chunk unnamed-chunk-18](figure/unnamed-chunk-18-1.png)

***.hint
Question prefaces a positive test result

***.explanation
1. Incorrect - Moving the line to the right increases the specificity because it captures more true negatives as a portion of total negative individuals
2. Incorrect - Moving the line to the right decreases the sensitivity because it captures fewer true positives as a portion of total positive individuals
3. Correct - Moving the line to the right increase positive predictive value drives up the portion of true positives to total positive test by reducing the number of false positives
4. Incorrect - The question is concerned about positives tests which do not factor into negative predictive value
5. Incorrect - The question is concerned about positives tests which do not factor into negative predictive value

--- &twocolumn

## Odds and risk connect disease with exposure

***=left

> - Odds 
  - Risk that someone with an exposure will get disease
> - Odds ratio (OR)
  - Excess odds of exposure of one population relative to another
> - Risk - __Must know disease prevalence__
  - __Probability__ that someone with an exposure will get a disease
> - Risk Ratio (Relative Risk or RR)
  - Excess risk of one population relative to another
> - Both significant if CI does not include 1

***=right

![](assets/img/contingency_table.png)

--- &radio
## Question #6

Investigators are studying the association between mesothelioma and asbestos exposure. Due to the relative rarity of the disease, they design a very large case-control study. In the end, they find an \(OR = 20 (19.54;20.52, p < 0.001)\). After assuming that the OR is a good approximation of risk, the authors conclude that the risk of mesothelioma is 20 times higher in those exposed to asbestos compared to control. Why is their assumption reasonable?

1. _The incidence of mesothelioma in the population is low_
2. The sample size of this study is very large
3. The result is highly significant
4. The OR is always a good approximation of outcome risk
5. The 95% CI is very narrow around the OR of 20

***.hint
Think about the denominators for odds and risks.

***.explanation
Give an explanation

--- &vcenter
## OR approximates RR in low prevalence diseases

![](assets/img/contingency_table.png)

--- &radio
## Question #7

Two studies were conducted on different samples from the same population to assess the relationship between oral contraceptive use and the risk of deep venous thrombosis (DVT). Study A showed an increased risk of DVT among oral contraceptive users, with a relative risk of 2.0 and a 95% CI of 1.2-2.8. Study B showed a relative risk of 2.05 and a 95% CI of 0.8-3.1. Which of the following statements is most likely to be true regarding these 2 studies?

1. The p-value in study B is likely to be < 0.05
2. The result in study A is not accurate
3. The result in study A is not statistically significant
4. The result in study B is likely biased
5. _The sample size is likely smaller in study B than study A_

***.hint
What gives a narrower confidence interval?

***.explanation
1. Incorrect - The CI in study B overlaps 1 so it is not significant
2. Incorrect - It is hard to judge accuracy without knowing the objective Truth
3. Inccorect - The CI in study A does not include 1 so it is statistically significant
4. Incorrect - There is no reason to believe B is biased
5. Correct - Per slide 23/38 bigger sample leads to improved ability to reject a false null hypothesis

--- &vcenter
## Attributable risk is a relative incidence difference
![plot of chunk unnamed-chunk-19](figure/unnamed-chunk-19-1.png)

--- &twocolumn
## Absolute risk reduction is a risk difference

<br>
***=left
> - Reminder
  - Exposed: \(Risk = A / (A + B)\)
  - Unexposed: \(Risk = C / (C + D)\)
<br><br>
> - \(AR = Risk_{Unexposed} - Risk_{Exposed}\)
> - \(ARR = Risk_{Control} - Risk_{Treatment}\)
<br><br>
> - Number needed to treat
  - Number of patients treated for __ONE__ patient benefited
  - \(NNT = 1 / ARR\)
  - FYI: \(NNH = 1 / AR\)

***=right
![plot of chunk unnamed-chunk-20](figure/unnamed-chunk-20-1.png)

--- .segue
## Types of Biases - My groupings

--- &vcenter
## Biases of design or unseen variables
> - Selection bias
  - Non-random partitioning of individuals into groups
> - Observer-expectancy
  - Observer is unblinded and expects a particular outcome
> - Hawthorne effect
  - Subjects improve health behaviors because someone is watching
> - Effect modification bias
  - Magnitude of effect varies by third variable
  - __Can__ be eliminated by stratification
> - Confounding
  - Unseen third variable is an underlying cause for correlation of two other variables
  - __Cannot__ be eliminated by stratification

--- &vcenter
## Biases of information (measurement)
> - Recall bias
  - Subjects with disease can recall exposures better than healthy subjects
> - Procedure bias
  - Experimenters vary systematically in the way they do work
  - e.g. Experimenters don't follow the specified procedure
> - Instrument bias
  - Instrument is broken
  - Instruments can also be things like surveys or __clerkship evaluations__
  - Just means instrument is not reliable

--- &vcenter
## Biases of time and completion
> - Lead-time bias
  - New test detects disease earlier
  - Survival appears improved with new test
> - Attrition bias
  - Subjects systematically withdraw
  - Could be things like side effects or lack of improvement
> - Loss-to-follow up
  - Subjects randomly do not report for scheduled followup

--- .segue
## Types of studies

--- &vcenter
## The pyramid of evidence is a hierarchy

![](assets/img/evidence_pyramid.jpg)

__Closer to the top means better evidence__

--- &vcenter
<div class="centered"><font size="7">Experimental Trials</font size></div>

--- &vcenter
## Randomized control trial is in the name
![](assets/img/randomized_control.png)

--- &vcenter
## Randomized control trials are the gold standard
> - This is widely considered the gold standard for clinical evidence
<br><br>
> - Question: __Primary__ purpose of randomization?
> - Answer: To eliminate __selection bias__
  - Selection bias is eliminated if randomization is technically correct
<br><br>
> - Question: Secondary goal of randomization?
> - Answer: To control confounders
  - Confounders are not necessarily eliminated even with perfect technical execution
<br><br>
> - Can use relative risk because investigator knows prevalence of exposure and disease

--- &vcenter
## Crossover trial means the two groups switch
![](assets/img/crossover.png)
<br><br>
 - This post hoc analysis is overly simplified for real life
 - This understanding is sufficient for step 1
 - Confounders reduced because a patient can serve as their own control

--- &vcenter
<div class="centered"><font size="7">Observational Studies</font size></div>

--- &vcenter
## Prospective cohorts follow groups into the future

![](assets/img/prospective_cohort.png)

--- &vcenter
## Retrospective cohorts follow groups from the past

![](assets/img/retrospective_cohort.png)

--- &vcenter
## Cohorts form the next level of evidence
 > - Can use relative risk because investigator knows prevalence of exposure and disease
 > - Subjects vary by exposure status
 <br><br>
 > - __Selection bias__ is the biggest problem
   - Investigator has infinite control over inclusion
 > - Other biases
   - Attrition, loss-to-follow up, confounding, Hawthorne
 <br><br>
 > - Retrospective
   - Information bias

--- &vcenter
## Case-control trials measure chance of exposure given disease

--- &vcenter
## Cross-sectional trials measure exposure and disease simultaneously

--- &vcenter
<div class="centered"><font size="7">The End</font size></div>

