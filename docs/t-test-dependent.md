# Compare means in two dependent groups

To compare the means in two dependent groups, the t-test for dependent groups can be used. In this example, a dataset/dataframe called `dat` contains two continuous variables called `dependentVariable_t0` and `dependentVariable_t1`

## SPSS

```
T-TEST PAIRS = dependentVariable_t0 WITH
               dependentVariable_t1 (PAIRED).
```

## R

```r
meanDiff(dependentVariable_t0, dependentVariable_t1,
         paired=TRUE);
```
