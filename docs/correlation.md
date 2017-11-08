# Correlation

To explore the association between two continuous variables, the correlation coefficient can be computed. In this example, a dataset/dataframe called `dat` contains two continuous variables, `independentVariable` and `dependentVariable`.

## SPSS

```
CORRELATIONS
  /VARIABLES = independentVariable dependentVariable.
```

## R

```r
cor.test(dat$independentVariable, dat$dependentVariable)
```
