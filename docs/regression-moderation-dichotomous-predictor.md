# Moderation with a dichotomous and a continous predictor

Moderation means that the causal association between two variables is itself influenced by a third variable. It is tested by analysing the interaction of the supposed predictor with the supposed moderator in their effects on the dependent variable. In this example, a dataset/dataframe called `dat` contains three variables, a continuous predictor called `independentVariable`, a dichotomous supposed moderator called `dichotomousVariable`, and a continuous dependent variable called `dependentVariable`.

## SPSS

Analysing an interaction in SPSS first requires creating a new variable consisting of the product of the two interacting variables (also see the section on [transformation](transformation.html)). Here this will be called `interactionTerm`. NOte that there is debate on whether the dichotomous predictor should be coded `0` and `1` or `-0.5` and `0.5`: this influences the interpretation of the resulting coefficients.

```
COMPUTE interactionTerm = dichotomousVariable * independentVariable.
```

The regression can then be conducted:

```
REGRESSION
  /DEPENDENT dependentVariable
  /METHOD ENTER independentVariable
                dichotomousVariable
                interactionTerm
  /STATISTICS COEF CI(95) R ANOVA.
```

To order a plot:

```
GRAPH
  /SCATTERPLOT=independentVariable WITH dependentVariable BY dichotomousVariable.
```

## R

R creates the interaction term automatically:

```r
regr(dependentVariable ~ independentVariable * dichotomousVariable,
     data=dat);
```

To also order a plot:

```r
regr(dependentVariable ~ independentVariable * dichotomousVariable,
     data=dat, plot=TRUE);
```
