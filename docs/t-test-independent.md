# Compare means in two independent groups

To compare the means in two independent groups, the t-test for independent groups can be used. In this example, a dataset/dataframe called `dat` contains a dichotomous variable `dichotomousVariable` that specifies group membership using `1` and `2` and a continuous dependent variable `dependentVariable`.

## SPSS

```
T-TEST
  /VARIABLES= dependentVariable
  /GROUPS=dichotomousVariable(1,2).
```

## R

```r
meanDiff(dat$dependentVariable, dat$dichotomousVariable)
```
