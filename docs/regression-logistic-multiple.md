# Logistic regression

To explore the association between multiple predictors and a dichotomous dependent variable, logistic regression analysis can be used. In this example, a dataset/dataframe called `dat` contains two continuous variables, `independentVariable` and `secondIndependentVariable`, and one dichotomous dependent variable `dichotomousVariable`.

## SPSS

```
LOGISTIC REGRESSION VARIABLES dichotomousVariable
  /METHOD=ENTER independentVariable + secondIndependentVariable.
```

## R

```r
logRegr(dichotomousVariable ~ independentVariable + secondIndependentVariable,
        data = dat);
```

To also show a plot, use:

```r
logRegr(dichotomousVariable ~ independentVariable + secondIndependentVariable,
        data = dat,
        plot = TRUE);
```
