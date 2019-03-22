# Standardizing a variable

Standardizing a variable means subtracting its mean from every data point in the data series, and the dividing the resulting numbers by the variable's standard deviation. The result is a variable with a mean of 0 and a standard deviation of 1.

In this example, a dataset/dataframe called `dat` contains a continuous variable called `independentVariable`.

## SPSS

This command orders descriptives, but the `/SAVE` subcommand also saves the standardized values. These are then given the original variable name prepended by `Z`, so in this case, `ZindependentVariable`:

```
DESCRIPTIVES  VARIABLES = independentVariable
 /SAVE.
```

## R

This stores the standardized values in a variable called `standardizedIndependentVariable`:

```
dat$standardizedIndependentVariable <-
  scale(dat$independentVariable);
```

In R is also easy to center a variable around its mean. The following command stores the centered values in a variable called `centeredIndependentVariable`:

```
dat$centeredVariable <-
  scale(dat$independentVariable, scale = FALSE);
```
