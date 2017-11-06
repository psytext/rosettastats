# Oneway anova

To compare the means in three or more independent groups, oneway analysis of variance is normally computed. In this example, a dataset/dataframe called `dat` contains a categorical variable `groupingVariable` and a continuous variable `dependentVariable`.

## SPSS

The simplest analysis uses a function called `ONEWAY`:

```
DATASET ACTIVATE dat.
ONEWAY dependentVariable BY groupingVariable.
```

However, to obtain an eta^2 effect size, a plot, or to test for equality of variances, the more powerful `UNIVARIATE` function must be used:

```
DATASET ACTIVATE dat.
UNIANOVA dependentVariable BY groupingVariable
  /PRINT=ETASQ HOMOGENEITY
  /PLOT=PROFILE(dependentVariable)
  /DESIGN=groupingVariable.
```

## R

To only obtain the analysis of variance results, use the `oneway` function and only specify both variables:

```r
oneway(dat$dependentVariable, dat$groupingVariable);
```

Additionally, descriptives, effect sizes, a plot, Levene's test, and corrections for heterogeneous variances can be requested:

```r
oneway(dat$dependentVariable, dat$groupingVariable,
       means = TRUE, levene = TRUE,
       corrections = TRUE, plot = TRUE);
```
