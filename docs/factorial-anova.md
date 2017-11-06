# Factorial anova

To compare the means in multiple groups defined by multiple categorical predictors (i.e. factors), factorial analysis of variance is normally used. In this example, a dataset/dataframe called `dat` contains categorical variables `groupingVariable` and `dichotomousVariable` and a continuous variable `dependentVariable`.

## SPSS

```
DATASET ACTIVATE dat.
UNIANOVA dependentVariable BY groupingVariable dichotomousVariable
  /PLOT = PROFILE(groupingVariable * dichotomousVariable)
  /DESIGN = groupingVariable D groupingVariable * dichotomousVariable.
```

## R

```r
fanova(dat,
       y = 'dependentVariable',
       between = c('groupingVariable',
                   'dichotomousVariable'),
       plot=TRUE)
```
