# Regression

To explore the association between multiple predictors and a continuous dependent variable, regression analysis can be used. In this example, a dataset/dataframe called `dat` contains three continuous variables, `independentVariable`, `secondIndependentVariable` and `dependentVariable`.

## SPSS

```
DATASET ACTIVATE dat.
REGRESSION
  /DEPENDENT dependentVariable
  /METHOD ENTER independentVariable secondIndependentVariable
  /STATISTICS COEF CI(95) R ANOVA.
```

## R

```r
regr(dependentVariable ~ independentVariable + secondIndependentVariable,
     data=dat);
```
