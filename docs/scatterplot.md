# Scatterplots

Scatterplots are normally used to inspect the association of two continuous variables. In this example, a dataset/dataframe called `dat` contains two continuous variables called `independentVariable` and `dependentVariable`.

## SPSS

```
GRAPH /SCATTERPLOT(BIVAR)=
  independentVariable WITH dependentVariable.
```

## R

```
scatterPlot(dat$independentVariable, dat$dependentVariable);
```
