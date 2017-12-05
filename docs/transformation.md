# Transformation

Transforming one or more variables means applying mathematical operators to change their values. Transformation can be used to change existing variables or create new variables out of (combinations of) other variables, for example when averaging a variable. In this example, a dataset/dataframe called `dat` contains a categorical variable `groupingVariable`, a dichotomous variable `dichotomousVariable`, and continuous variables `dependentVariable`, `independentVariable`, and `secondIndependentVariable`.

The common mathematical operators are `+` for addition, `-` for subtraction, `*` for multiplication, `/` for division, and `^` to raise a value to the power of another value. In more complex expressions, these operators are combined with parentheses to explicitly indicate precedence. In addition, a number of functions are available, but the names of those functions will generally differ between statistical packages.

## SPSS

The command used for applying mathematical operators to one or several variables in SPSS is called `COMPUTE`. It can be used in combination with mathematical operators:

```
COMPUTE newVariable = 2 * dependentVariable.
```

The mean of two variables can therefore be computed like this:

```
COMPUTE meanDependentVariable =
  (independentVariable + secondIndependentVariable) / 2.
```

But there is also a dedicated function available for this:

```
COMPUTE meanDependentVariable =
  MEAN(independentVariable, secondIndependentVariable).
```

This second function has a number of variations that allow efficiently dealing with missing values, by explicitly indicating how many values have to be valid to allow a nonmissing result. For example:

```
COMPUTE meanDependentVariable =
  MEAN.2(independentVariable, secondIndependentVariable).
```

In this example, `meanDependentVariable` will be missing for all cases where either `independentVariable`, `secondIndependentVariable`, or both is missing.

Similarly, adding variables together can be done either using the `+` operator, or using the `SUM` function, potentially appending a period followed by a number to indicate how many variables must have valid values in order to produce a nonmissing result. The following two commands would yield identical results:

```
COMPUTE sumDependentVariable =
  independentVariable + secondIndependentVariable.
  
COMPUTE sumDependentVariable =
  SUM(independentVariable, secondIndependentVariable).
```

## R

In R, mathematical operators can be used directly:

```r
dat$newVariable <- 2 * dat$dependentVariable;
dat$meanDependentVariable <- 
  (dat$independentVariable + dat$secondIndependentVariable) / 2;
```

Functions for computing means and sums also exist, for example `validMeans` and `validSums`:

```r
dat$meanDependentVariable <- 
  validMeans(dat$independentVariable, dat$secondIndependentVariable);
dat$meanDependentVariable <- 
  validSums(dat$independentVariable, dat$secondIndependentVariable);
```

In these functions, argument `requiredValidValues` can be used to specify which proportion (if `requiredValidValues` has a value lower than 1) or number (if `requiredValidValues` has a value of 1 or higher) of variables must have nonmissing values to compute the result:

```r
dat$meanDependentVariable <- 
  validMeans(dat$independentVariable, dat$secondIndependentVariable,
             requiredValidValues = 2);
dat$meanDependentVariable <- 
  validSums(dat$independentVariable, dat$secondIndependentVariable,
             requiredValidValues = 2);
```

