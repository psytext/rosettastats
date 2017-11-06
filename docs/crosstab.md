# Crosstable

To compare look at the association between two categorical variables, crosstables can be used. In this example, a dataset/dataframe called `dat` contains a categorical variable `groupingVariable` and contains a categorical variable `dichotomousVariable`.

## SPSS

```
DATASET ACTIVATE dat.
CROSSTABS 
  /TABLES=groupingVariable BY dichotomousVariable
  /STATISTICS=CHISQ CC PHI LAMBDA ETA CORR GAMMA D.
```

## R

```r
crossTab(dat$groupingVariable, dat$dichotomousVariable);
```
