# Mediation

Mediation analysis the the modeling of a hypothesized causal effect that operates through an intermediate ('mediating') variable. Note that mediation by definition entails strong assumptions regarding causality, which require longitudinal designs and almost always experimental independent manipulation of the predictor and mediator. In these examples, the dataset/dataframe is called `dat`, the predictor (the first variable in the causal chain) is called `predictorVariable`), the mediators are called `mediatorVariable1` and `mediatorVariable2` (the intermediate variables in the causal chain), the dependent variable is called `dependentVariable` (the last variable in the causal chain), and covariates are called `covariate1` and `covariate2`.

## SPSS

In SPSS the PROCESS macro can be used to analyse a mediation model. This macro can be downloaded from http://www.afhayes.com. The are several mediators possible and also several covariates. Example 1 has two mediators and no covariates.

```
PROCESS vars = dependentVariable,
               predictorVariable,
               mediatorVariable1,
               mediatorVariable2
   / y = dependentVariable
   / x = predictorVariable
   / m = mediatorVariable1
         mediatorVariable2
   / model = 4.

```

Example 2 has three mediators and two covariates.

```
PROCESS vars = dependentVariable,
               predictorVariable,
               mediatorVariable1,
               mediatorVariable2,
               mediatorVariable3,
               covariate1
               covariate2
   / y = dependentVariable 
   / x = predictorVariable 
   / m = mediatorVariable1
         mediatorVariable2
         mediatorVariable3
   / c = covariate1
         covariate2
   / model = 4.

```

## R

In R the fucntion is called `mediationSem`, which uses the SEM package `lavaan`. The data are in dataset `dat`. Example 1 is called as follows.

```r

mediationSem(dat = dat, 
             xvar  ="predictorVariable", 
             mvars = c("mediatorVariable1","mediatorVariable2"), 
             yvar  = "dependentVariable", );
```

In example 2 it is possible to choose on which variable (mediators or dependent) have an assumed effect. In this example the covariates have an assumed effect on both the mediators and the dependent variable.

```r

mediationSem(dat = dat, 
             xvar ="predictorVariable", 
             mvars = c("mediatorVariable1",
                       "mediatorVariable2",
                       "mediatorVariable3"), 
             yvar = "dependentVariable", 
             cmvars = c("covariate1",
                        "covariate2"), 
             cyvars = c("covariate1",
                        "covariate2"), );
```

The output can be put in an object and with for example the `r summary()` function the Lavaan output can be inspected.

```r

output <- mediationSem(dat = dat, 
                       xvar = "predictorVariable", 
                       mvars = c("mediatorVariable1",
                                 "mediatorVariable2",
                                 "mediatorVariable3"), 
                       yvar = "dependentVariable");
summary(output);
```
