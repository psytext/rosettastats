# Frequencies

Frequencies are normally viewed for categorical variables. In this example, a dataset/dataframe called `dat` contains variables called `groupingVariable` and `dichotomousVariable`.

## SPSS

```
FREQ VARIABLES=groupingVariable.
```

To also order a barchart, use:

```
FREQ VARIABLES=groupingVariable
  /BARCHART FREQ.
```

To order frequencies for multiple variables simultaneously, use:

```
FREQ VARIABLES=groupingVariable dichotomousVariable.
```

## R

```
freq(dat$groupingVariable);
```

To also order a barchart, use:

```
freq(dat$groupingVariable, plot=TRUE);
```

To order frequencies for multiple variables simultaneously, use:

```
frequencies(dat$groupingVariable, dat$dichotomousVariable);
```

