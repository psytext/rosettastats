# Recoding a variable

Recoding is the task of changing values of a variable to other values. In this example, variable `x` is recoded and the new variable is stored in `x_new`. This variable is assume to exist in a dataset (dataframe in R) called `dat`. Variable `x` has five possible values: 1, 2, 3, 4 and 5. This recoding command inverses the variable (i.e. 5 becomes 1, 4 becomes 2, 3 stays the same, 2 becomes 4, and 1 becomes 5).

## SPSS

```
DATASET ACTIVATE dat.
RECODE x (1=5) (2=4) (3=3) (4=2) (5=1) INTO x_new.
EXECUTE.
```

## R

```r
require(car);
dat$x_new <- Recode(dat$x, "1=5; 2=4; 3=3; 4=2; 5=1");
```
