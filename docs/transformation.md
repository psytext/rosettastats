# Transformation

Transforming one or more variables means applying mathematical operators to change their values. Transformation can be used to change existing variables or create new variables out of (combinations of) other variables, for example when averaging a variable. In this example, a dataset/dataframe called `dat` contains a categorical variable `groupingVariable`, a dichotomous variable `dichotomousVariable`, and continuous variables `dependentVariable`, `independentVariable`, and `secondIndependentVariable`.

The common mathematical operators are `+` for addition, `-` for subtraction, `*` for multiplication, `/` for division, and `^` to raise a value to the power of another value. In more complex expressions, these operators are combined with parentheses to explicitly indicate precedence. In addition, a number of functions are available, but the names of those functions will generally differ between statistical packages.

## SPSS

The command used for applying mathematical operators to one or several variables in SPSS is called `COMPUTE`. It can be used in combination with mathermatical operators:

```
COMPUTE newVariable = 2 * dependentVariable.
```

The mean of two variables can therefore be computed like this:

```
COMPUTE meanDependentVariable = (independentVariable + secondIndependentVariable) / 2.
```

But there is also a dedicated function available for this:

```
COMPUTE meanDependentVariable = MEAN(independentVariable, secondIndependentVariable).
```

This second function 


## R

```r
crossTab(dat$groupingVariable, dat$dichotomousVariable);
```
