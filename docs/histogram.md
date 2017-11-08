# Histograms

Histograms are normally used to inspect the distribution of continuous categorical variables. In this example, a dataset/dataframe called `dat` contains a variable called `dependentVariable`.

## SPSS

```
GRAPH /HISTOGRAM(NORMAL) = dependentVariable.
```

## R

```
powerHist(dat$dependentVariable);
```

