# Histograms

Histograms are normally used to inspect the distribution of continuous (cardinal, e.g. interval or ratio-level) variables. In this example, a dataset/dataframe called `dat` contains a variable called `dependentVariable`.

## SPSS

```
GRAPH /HISTOGRAM(NORMAL) = dependentVariable.
```

## R

```r
powerHist(dat$dependentVariable);
```

