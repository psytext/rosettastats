# Renaming a variable

In this example, a dataset/dataframe called `dat` contains a variable called `independentVariable` that we want to rename to `freshlyRenamedVariable`.

## SPSS

```
RENAME VARIABLES independentVariable =
  freshlyRenamedVariable.
```

## R

```
names(dat)[names(dat) == 'independentVariable'] <-
  'freshlyRenamedVariable';
```

You can also use for example the package "dplyr", which makes the code more intuitive.

## R

```
require(dplyr)

dat <- rename(dat, freshlyRenamedVariable = independentVariable);
```

