# Repeated measures anova

To compare changes in means over time, repeated measures anova can be used. In this example, a dataset/dataframe called `dat` contains a categorical independent variable `groupingVariable`, and contains the data for the continuous variable in three variables, each corresponding to a measurement moment, respectively `dependentVariable_t0`, `dependentVariable_t1`, and `dependentVariable_t2`.

## SPSS

```
DATASET ACTIVATE dat.
GLM
  /dependentVariable_t0 dependentVariable_t1 dependentVariable_t2
  /WSFACTOR= groupingVariable 3 Simple
  /WSDESIGN= groupingVariable
  /PRINT=DESCRIPTIVES ETASQ
```

## R

```r
fanova(dat,
       y = c('dependentVariable_t0',
             'dependentVariable_t1',
             'dependentVariable_t2'),
       between = 'groupingVariable')
```
