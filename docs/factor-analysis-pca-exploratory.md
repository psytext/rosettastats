# Exporatory principal components analysis

In this example, the principal components analysis will be conducted on dataset/dataframe called `dat` containing ten variables that represent data collected with ten questions. These ten variables are called `item1`, `item2`, `item3`, `item4`, `item5`, `item6`, `item7`, `item8`, `item9`, and `item10`.

## SPSS

To perform the principal components analysis, use:

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
  /EXTRACTION PCA
  /CRITERIA ITERATE(25)
  /ROTATION VARIMAX
  /METHOD=CORRELATION.
```

To extract a specific number of components, for example three components, replace `EIGEN(1)` by `FACTORS(3)`.

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
  /EXTRACTION PCA
  /CRITERIA ITERATE(25)
  /ROTATION VARIMAX
  /METHOD=CORRELATION.
  /FORMAT=SORT BLANK(.3).
```

## R

To perform the principal components analysis, use:

```r
facComAnalysis(dat,
               items=c('item1', 'item2', 'item3',
                       'item4', 'item5', 'item6',
                       'item7', 'item8', 'item9',
                       'item10'),
               fm='pca',
               rotate='varimax');
```

To extract a specific number of components, for example three components, use:

```r
facComAnalysis(dat,
               items=c('item1', 'item2', 'item3',
                       'item4', 'item5', 'item6',
                       'item7', 'item8', 'item9',
                       'item10'),
               fm='pca',
               rotate='varimax,
               nfactors = 3);
```

To suppress the printing of factor loadings lower than a specific value, for example .3, use:

```r
facComAnalysis(dat,
               items=c('item1', 'item2', 'item3',
                       'item4', 'item5', 'item6',
                       'item7', 'item8', 'item9',
                       'item10'),
               fm='pca',
               rotate='varimax',
               maskLoadingsUnder = .3);
```
