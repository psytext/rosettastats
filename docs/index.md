Rosetta Stats
=============

This site is meant to illustrate how common analyses can be conducted in a variety of statistical software packages. It was founded mainly to facilitate using SPSS and R in parallel.

## Important information to read first

It can be necessary to execute one or more commands before analyses can be conducted. Instead of repeating those commands in every example, they are provided here.

### SPSS

Before running commands in SPSS, two things are first required. First, the data have to be loaded (see the dedicated section below). Second, that dataset must be activated. In this example, we will assume the dataset is called `dat`:

```
DATASET ACTIVATE dat.
```

### R

Most examples here use an R package called `userfriendlyscience` because it contains a large number of functions designed to act similar to their SPSS counterparts. This package, therefore, first has to be installed:

```
install.packages('userfriendlyscience');
```

This only has to happen once: after it has been installed, it will remain available. However, it will still have to be loaded in every R session using:

```
require('userfriendlyscience');
```

In addition, the data have to be loaded (see the dedicated section below).

## Loading data

- [Loading data from a file](loading-data-from-file.html)

## Data preprocessing

Before analyses can be conducted, it is sometimes necessary to perform some preprocessing.

- [Recoding a variable](recoding.html)

## Univariate analyses

Univariate analyses are analyses of only one variable, for example to inspect distributions or frequencies.

- [Descriptives](descriptives.html)
- [Descriptives split by group](descriptives-by-group.html)

## Bivariate analyses

Bivariate analyses are analyses of associations between two variables.

- Two continuous variables: [correlation](correlation.html) and [regression](regression-single.html)
- One dichotomous variable, one continuous variable: [independent-samples t-test](t-test-independent.html)
- One categorical variable, one continuous variable: [oneway analysis of variance](anova-oneway.html)
- Two categorical variables: [crosstable](crosstab.html)

## Multivariate analyses

Multivariate analyses involve more than two variables.

- [Regression analysis](regression-multiple.html)
- [Factorial analysis of variance](anova-factorial.html)
- [Repeated measures analysis of variance](anova-repeated-measures.html)

<!-- ## Intensive longitudinal analyses -->
