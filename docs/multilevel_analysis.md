# Multillevel analysis

Multilevel analysis (MLA) is used for the analysis of hierarchical data. Data at the lowest level are clustered in higher levels. An important application for MLA is in ESM/EMA data. This type of data are called intensive longitudinal data. Subjects have measurements on multiple occasions. The occasions are clustered within the subjects. In these examples, the dataset/dataframe is called `dat`, the predictor  is called `predictorVariable`(more than one are possible), the clustervariables are called `idVariable1`, the dependent variable is called `dependentVariable`. For longitudinal data there is an `indexVariable`, which indicates the repeated measures. Furthermore, you may need a lagged variable to control for autocorrelation: for example, a lagged one variable: `predictorVariableLag1`.

## SPSS

In SPSS the MIXED procedure can be used to do multilevel analysis. A simple model with one predictor and two random efffects, for respectively the intercept and the predictor, can be run with the following syntax.

```
MIXED dependentVariable  WITH predictorVariable
  /PRINT= SOLUTION TESTCOV
  /METHOD= ML
  /FIXED= INTERCEPT predictorVariable 
  /RANDOM= INTERCEPT predictorVariable| SUBJECT(idVariable)  COVTYPE(UN).


```

Example 2 shows a longitudinal example.

```
MIXED dependentVariable WITH predictorVariable indexVariable
  /PRINT=SOLUTION TESTCOV
  /FIXED=INTERCEPT predictorVariable | SSTYPE(3)
  /RANDOM=INTERCEPT  predictorVariable | SUBJECT(idVariable2) COVTYPE(VC)
  /REPEATED=indexvariable  | SUBJECT(idVariable) COVTYPE(AR1).

```

## R

In R the function is called `lmer`, which is in the  package `lme4`. The data are in dataset `dat`. Example 1 is called as follows. So, make sure to install the `lme4` package first and load it in your R session with `library(lme4)`.

```r


  model <- lmer(dependentVariable ~ predictorVariable + 
               (1 + predictorVariable| idVariable, data = dat)
  
```

Example 2 is called with the following code.

```r

  model <- lmer(dependentVariable ~ predictorVariable + predictorVariableLag1 +
               (1 + predictorVariable| idVariable, data = dat)
 
```

The output can be put in an object and with, for example, the `r summary()` function this output can be inspected.

```r

summary(model);

```
