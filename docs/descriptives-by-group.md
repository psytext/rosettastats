# Descriptives by group

Descriptives are statistics that briefly summarize data series. These examples show how to order descriptives for a variable called `dependentVariable` in a dataset/dataframe called `dat`, where the descriptives are shown separately for each group, designated by variable `groupingVariable`.

## SPSS

```
DATASET ACTIVATE dat.
EXAMINE VARIABLES = dependentVariable BY groupingVariable
  /PLOT = Boxplot Histogram.
```

## R

```r
examineBy(dat$dependentVariable, by=dat$groupingVariable);
```
