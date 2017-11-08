# Exporatory factor analysis

In this example, factor analysis will be conducted on dataset/dataframe called `dat` containing ten variables that represent data collected with ten questions. These ten variables are called `item1`, `item2`, `item3`, `item4`, `item5`, `item6`, `item7`, `item8`, `item9`, and `item10`.

## SPSS

To perform the factor analysis, use:

```
FACTOR
  /VARIABLES item1 item2 item3 item4 item5
             item6 item7 item8 item9 item10
  /MISSING LISTWISE 
  /ANALYSIS item1 item2 item3 item4 item5
            item6 item7 item8 item9 item10
  /PRINT INITIAL ROTATION
  /PLOT EIGEN
  /CRITERIA EIGEN(1) ITERATE(25)
  /EXTRACTION PAF
  /CRITERIA ITERATE(25)
  /ROTATION OBLIMIN
  /METHOD=CORRELATION.
```

The rotation method can be changed by specifying, for example, `VARIMAX`. To extract a specific number of factors, for example three factors, replace `EIGEN(1)` by `FACTORS(3)`.

To suppress the printing of factor loadings lower than a specific value, for example .3, use:

```
FACTOR
  /VARIABLES item1 item2 item3 item4 item5
             item6 item7 item8 item9 item10
  /MISSING LISTWISE 
  /ANALYSIS item1 item2 item3 item4 item5
            item6 item7 item8 item9 item10
  /PRINT INITIAL ROTATION
  /PLOT EIGEN
  /CRITERIA EIGEN(1) ITERATE(25)
  /EXTRACTION PAF
  /CRITERIA ITERATE(25)
  /ROTATION OBLIMIN
  /METHOD=CORRELATION.
  /FORMAT=SORT BLANK(.3).
```

## R

To perform the factor analysis, use:

```r
facComAnalysis(dat,
               items=c('item1', 'item2', 'item3',
                       'item4', 'item5', 'item6',
                       'item7', 'item8', 'item9',
                       'item10'),
               rotate='oblimin');
```

The rotation method can be changed by specifying, for example, `varimax`. To extract a specific number of factors, for example three factors, use:

```r
facComAnalysis(dat,
               items=c('item1', 'item2', 'item3',
                       'item4', 'item5', 'item6',
                       'item7', 'item8', 'item9',
                       'item10'),
               rotate='oblimin,
               nfactors = 3);
```

To suppress the printing of factor loadings lower than a specific value, for example .3, use:

```r
facComAnalysis(dat,
               items=c('item1', 'item2', 'item3',
                       'item4', 'item5', 'item6',
                       'item7', 'item8', 'item9',
                       'item10'),
               rotate='oblimin',
               maskLoadingsUnder = .3);
```
