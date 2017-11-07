# Moderation with a dichotomous and a continous predictor

Moderation means that the causal association between two variables is itself influenced by a third variable. It is tested by analysing the interaction of the supposed predictor with the supposed moderator in their effects on the dependent variable. In this example, a dataset/dataframe called `dat` contains three variables, a continuous predictor called `independentVariable`, a dichotomous supposed moderator called `dichotomousVariable`, and a continuous dependent variable called `dependentVariable`.

## SPSS

Analysing an interaction in SPSS first requires creating a new variable consisting of the product of the two interacting variables (also see the section on [transformation](transformation.html)).

```
DATASET ACTIVATE dat.
REGRESSION
  /DEPENDENT dependentVariable
  /METHOD ENTER independentVariable secondIndependentVariable
  /STATISTICS COEF CI(95) R ANOVA.
```

To order a plot:

```
GRAPH
  /SCATTERPLOT=independentVariable WITH dependentVariable BY secondIndependentVariable.
```

Note that this only works if the second variable, `secondIndependentVariable`, is categorical. If it is continuous, it is probably a good idea to create a categorical variable to enable visualisation.

## R

```r
regr(dependentVariable ~ independentVariable * secondIndependentVariable,
     data=dat);
```

To also order a plot:

```r
regr(dependentVariable ~ independentVariable * secondIndependentVariable,
     dat=dat, plot=TRUE);
```
