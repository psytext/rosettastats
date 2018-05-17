# Renaming a variable

In this example, a dataset/dataframe called `dat` contains a variable called `oldVariable` that we want to rename to `newVariable`.

## SPSS

```
RENAME VARIABLES oldVariable = newVariable.
```

## R

```
names(dat)[names(dat) == 'oldVariable'] <- 'newVariable';
```

You can also use for example the package "dplyr", which makes the code more intuitive.

## R

```
require(dplyr)

dat <- rename(dat, newVariable = oldVariable);
```

