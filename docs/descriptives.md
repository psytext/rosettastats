# Descriptives

Descriptives are statistics that briefly summarize data series. These examples show how to order descriptives for a variable called `dependentVariable` in a dataset/dataframe called `dat`.

## SPSS

```
DATASET ACTIVATE dat.
EXAMINE VARIABLES=dependentVariable
  /PLOT = Boxplot Histogram.
```

## R

```r
examine(dat$dependentVariable);
```
