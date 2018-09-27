# Moderated mediation

Mediation refers to a causal model in which the relation between the predictor and the dependent variable is mediated by one or more other variables ("the mediators). Note that mediation by definition entails strong assumptions regarding causality, which require longitudinal designs and almost always experimental independent manipulation of the predictor (and if possible mediator). 
The causal path between the predictor and the mediator(s) can be moderated by a moderator. Likewise, the path between the mediators and the dependent variable can be moderated by another moderator. A moderator strengthens or weakens the relation between two variables.
In these examples, the dataset/dataframe is called `dat`, the predictor (the first variable in the causal chain) is called `predictorVariable`, the mediators are called `mediatorVariable1`, `mediatorVariable2`, etc. (the intermediate variables in the causal chain), the dependent variable is called `dependentVariable` (the last variable in the causal chain), and covariates are called `covariate1`, `covariate2`, etc.

## SPSS

In SPSS the PROCESS macro can be used to analyse a (moderated) mediation model. Version 3 of this macro can be downloaded from http://www.afhayes.com. The SPSS code shown here is based on version 2. Several mediators can be added and also several covariates. A model code must be specified in this version. See Hayes(2013). 

Example 1 has two mediators and no covariates.

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

Example 2 has one mediator, one moderator of the path from the predictor to the mediator (the x-m path) and no covariates.

```
PROCESS vars = dependentVariable, predictorVariable mediatorVariable, moderatorVariable
   / y = dependentVariable
   / x = predictorVariable
   / m = mediatorVariable 
   / w = moderatorVariable
   / model = 7.

```

Example 3 has one mediator, one moderator of the path from the mediator to the dependent variable (m-y path) and two covariates.

```
PROCESS vars = dependentVariable, predictorVariable mediatorVariable1,moderatorVariable, covariate1 covariate2
   / y = dependentVariable 
   / x = predictorVariable 
   / m = mediatorVariable 
   / v = moderatorVariable
   / c = covariate1 covariate2
   / model = 14.

```

Example 4 has two mediators, two moderators one for each path and two covariates.

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
Example 1 is a mediation model with two mediators and without moderator and is called as follows.

```r

moderatedMediationSem(dat = dat, 
                      xvar  ="predictorVariable", 
                      mvars = c("mediatorVariable1","mediatorVariable2"), 
                      yvar  = "dependentVariable", );
```


In example 2 a moderator of the x-m path is added to the model, which is called as follows.

```r

moderatedMediationSem(dat = dat, 
                      yvar  = "dependentVariable",
                      xvar  = "predictorVariable", 
                      mvars = "mediatorVariable", 
                      xmmod = "moderatorVariable");
```

It is possible to choose on which variabele (mediators or dependent) the covariates have an assumed effect.
In this example both covariates have an assumed effect on both the mediators and the dependent variable. Furthermore, the m-y path is moderated.
Example 3 is called as follows.

```r

moderatedMediationSem(dat = dat, 
                      yvar  = "dependentVariable",
                      xvar  = "predictorVariable", 
                      mvars = "mediatorVariable", 
                      mymod = "moderatorVariable",
                      cmvars = c("covariate1","covariate2"),
                      cyvars = c("covariate1","covariate2") );
```

In example 4 both x-m and m-y paths are moderated. There are two mediators.
In this example the covariates have an assumed effect on both the mediators and the dependent variable.
Furthermore plots that show the simple slopes of the indirect effects are requested.
Example 4 is called as follows.

```r

moderatedMediationSem(dat = dat, 
                      yvar  = "dependentVariable", 
                      xvar  ="predictorVariable", 
                      mvars = c("mediatorVariable1","mediatorVariable2"), 
                      xmmod = "moderatorVariable1",
                      mymod = "moderatorVariable2",
                      cmvars = c("covariate1","covariate2"), 
                      cyvars = c("covariate1","covariate2");
             
```

The output can be put in an R object and can then be further inspected. The two functions ' print() ' and ' plot() ' are  developped to provide relevant output of this analysis.
The ' plot() ' function is only relevant when there is moderation, because it shows the simple slopes.

```r

output <- moderatedMediationSem(dat = dat, 
                                xvar  ="predictorVariable", 
                                mvars = c("mediatorVariable1","mediatorVariable2"), 
                                yvar  = "dependentVariable"
                                xmmod = "moderatorVariable") ;

print(output)
plot(output);         
             
             
```




