# Moderated mediation

Moderation and mediation models can also be combined. The path from predictor to mediator can be moderated by a moderator designated as "w", while the path from mediator to dependent variable can be moderated by a moderator designated as "v". The PROCESS macro uses different model numbers to distinguish these models. The R function moderatedMediationSem uses named paramters to distinguish the two models.

## SPSS

In SPSS the PROCESS macro can be used to analyse a moderated mediation model. This macro can be downloaded from http://www.afhayes.com.
The are several mediators possible and also several covariates. 
Example 1 has one mediator, one moderator of the path from the predictor to the mediator and no covariates.

```
PROCESS vars = dependentVariable, predictorVariable mediatorVariable, moderatorVariable
   / y = dependentVariable
   / x = predictorVariable
   / m = mediatorVariable 
   / w = moderatorVariable
   / model = 7.

```

Example 2 has one mediator, one moderator of the path from the mediator to the dependent variable and two covariates.

```
PROCESS vars = dependentVariable, predictorVariable mediatorVariable1,moderatorVariable, covariate1 covariate2
   / y = dependentVariable 
   / x = predictorVariable 
   / m = mediatorVariable 
   / v = moderatorVariable
   / c = covariate1 covariate2
   / model = 14.

```

Example 3 has two mediators, two moderators one for each path and two covariates.

```
PROCESS vars = dependentVariable, predictorVariable mediatorVariable1,moderatorVariable, covariate1 covariate2
   / y = dependentVariable 
   / x = predictorVariable 
   / m = mediatorVariable1 mediatorVariable22
   / w = moderatorVariable1
   / v = moderatorVariable2
   / c = covariate1 covariate2
   / model = 21.
```

## R

In R the function is called moderatedMediationSem, which uses the SEM package Lavaan.
The data are in dataset "dat".
Example 1 is called as follows.

```r

moderatedMediationSem(dat = dat, 
             yvar  = "dependentVariable",
             xvar  = "predictorVariable", 
             mvars = "mediatorVariable", 
             xmmod = "moderatorVariable");
```

It is possible to choose on which variabele (mediators or dependent) the covariates have an assumed effect.
In this example both covariates have an assumed effect on both the mediators and the dependent variable. Furthermore, the m-y path is moderated.
Example 2 is called as follows.

```r

moderatedMediationSem(dat = dat, 
             yvar  = "dependentVariable",
             xvar  = "predictorVariable", 
             mvars = "mediatorVariable", 
             mymod = "moderatorVariable",
             cmvars = c("covariate1","covariate2"),
             cyvars = c("covariate1","covariate2") );
```

In example 3 both x-m and m-y paths are moderated. There are two mediators.
In this example the covariates have an assumed effect on both the mediators and the dependent variable.
Furthermore plots that show the simple slopes of the indirect effects are requested.
Example 3 is called as follows.

```r

moderatedMediationSem(dat = dat, 
             yvar  = "dependentVariable", 
             xvar  ="predictorVariable", 
             mvars = c("mediatorVariable1","mediatorVariable2"), 
             xmmod = "moderatorVariable1",
             mymod = "moderatorVariable2",
             cmvars = c("covariate1","covariate2"), 
             cyvars = c("covariate1","covariate2"),
             plot = TRUE);
```

The output can be put in an object and with for example the `r summary()` function the Lavaan output can be inspected.

```r

output <- moderatedMediationSem(dat = dat, 
             xvar  ="predictorVariable", 
             mvars = c("mediatorVariable1","mediatorVariable2"), 
             yvar  = "dependentVariable"
             xmmod = "moderatorVariable") ;

summary(output);         
             
             
```




