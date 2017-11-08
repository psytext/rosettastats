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
