# Mediation

Descriptives are statistics that briefly summarize data series. These examples show how to order descriptives for a variable called `dependentVariable` in a dataset/dataframe called `dat`, where the descriptives are shown separately for each group, designated by variable `groupingVariable`.

## SPSS

In SPSS the PROCESS macro can be used to analyse a mediation model. This macro can be downloaded from http://www.afhayes.com.
The are several mediators possible and also several covariates. 
Example 1 has two mediators and no covariates.

```
PROCESS vars = dependentVariable, predictorVariable mediatorVariable1,mediatorVariable2
   / y = dependentVariable
   / x = predictorVariable
   / m = mediatorVariable1 mediatorVariable2
   / model = 4.

```

Example 2 has three mediators and two covariates.

```
PROCESS vars = dependentVariable, predictorVariable mediatorVariable1,mediatorVariable2, mediatorVariable3, covariate1 covariate2
   / y = dependentVariable 
   / x = predictorVariable 
   / m = mediatorVariable1 mediatorVariable2 mediatorVariable3
   / c = covariate1 covariate2
   / model = 4.

```

## R

In R the function is called mediationSem, which uses the SEM package Lavaan.
The data are in dataset "dat".
Example 1 is called as follows.

```r

mediationSem(dat = dat, 
             xvar  ="predictorVariable", 
             mvars = c("mediatorVariable1","mediatorVariable2"), 
             yvar  = "dependentVariable", );
```

In example 2 it is possible to choose on which variabele (mediators or dependent) have an assumed effect.
In this example the covariates have an assumed effect on both the mediators and the dependent variable.

```r

mediationSem(dat = dat, 
             xvar  ="predictorVariable", 
             mvars = c("mediatorVariable1","mediatorVariable2","mediatorVariable3"), 
             yvar  = "dependentVariable", 
             cmvars = c("covariate1","covariate2"), 
             cyvars = c("covariate1","covariate2"), );
```

The output can be put in an object and with for example the `r summary()` function the Lavaan output can be inspected.

```r

output <- mediationSem(dat = dat, 
             xvar  ="predictorVariable", 
             mvars = c("mediatorVariable1","mediatorVariable2","mediatorVariable3"), 
             yvar  = "dependentVariable") ;

summary(output);         
             
             
```




