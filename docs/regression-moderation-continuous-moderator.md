# Moderation with two continous predictors

Moderation means that the causal association between two variables is itself influenced by a third variable. It is tested by analysing the interaction of the supposed predictor with the supposed moderator in their effects on the dependent variable. In this example, a dataset/dataframe called `dat` contains three variables, two continuous predictor called `independentVariable` and `secondIndependentVariable`, and a continuous dependent variable called `dependentVariable`.

## SPSS

Analysing an interaction in SPSS first requires creating a new variable consisting of the product of the two interacting variables (also see the section on [transformation](transformation.html)). Here this will be called `interactionTerm`. Note that this often introduces collinearity, which can be ameliorated by standardizing the predictors first (also see the section on [standardizing](standardizing.html)).

```
DESCRIPTIVES  VARIABLES = independentVariable secondIndependentVariable
 /SAVE.
COMPUTE interactionTerm = ZindependentVariable * ZsecondIndependentVariable.
```

The regression can then be conducted:

```
REGRESSION
  /DEPENDENT dependentVariable
  /METHOD ENTER independentVariable
                secondIndependentVariable
                interactionTerm
  /STATISTICS COEF CI(95) R ANOVA.
```

## R

R creates the interaction term automatically:

```r
regr(dependentVariable ~ independentVariable * secondIndependentVariable,
     data=dat);
```

To also order a plot:

```r
regr(dependentVariable ~ independentVariable * secondIndependentVariable,
     data=dat, plot=TRUE);
```
