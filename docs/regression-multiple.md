# Regression

To explore the association between two continuous variables, regression analysis can be used. In this example, a dataset/dataframe called `dat` contains two continuous variables, `independentVariable` and `dependentVariable`.

## SPSS

```
DATASET ACTIVATE dat.
REGRESSION
  /DEPENDENT dependentVariable
  /METHOD ENTER independentVariable
  /STATISTICS COEF CI(95) R ANOVA.
```

## R

```r
regr(dependentVariable ~ independentVariable, data=dat);
```

To also order a plot:

```r
regr(dependentVariable ~ independentVariable, dat=dat, plot=TRUE);
```
