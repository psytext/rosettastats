# Reliability

Although reliability typically inevitably involves repeated measurement over time, approximations exist that are acceptable under the assumption that the error variance introduced within a single administration of an operationalisation is equal to the error variance introduced in repeated administrations (in other words, under the assumption that time does not introduce additional error variance). This latter category includes, for example, the widely used but also widely discouraged coefficient Alpha. In this example, Alpha and other reliability coefficients will be computed using a dataset/dataframe called `dat` containing ten variables that represent data collected with ten questions that together form one operationalisation. These ten variables are called `item1`, `item2`, `item3`, `item4`, `item5`, `item6`, `item7`, `item8`, `item9`, and `item10`.

## SPSS

To compute coefficient Alpha, use:

```
RELIABILITY
  /VARIABLES=item1 item2 item3 item4 item5
             item6 item7 item8 item9 item10
  /MODEL=ALPHA.
```

Instead of `ALPHA`, it is also possible to specify other underlying models such as `SPLIT` for the split-half reliability and `GUTTMAN` to compute Guttman's lower bound. To also order the corrected item-total correlations, as well as the item-corrected scale means, standard deviations, and alpha coefficients, use:

```
RELIABILITY
  /VARIABLES=item1 item2 item3 item4 item5
             item6 item7 item8 item9 item10
  /MODEL=ALPHA
  /SUMMARY=TOTAL.
```

## R

The function `scaleStructure` computes coefficient Alpha as well as a number of other coefficients such as Omega and coefficient H:

```r
reliability(dat,
            items=c('item1', 'item2', 'item3',
                    'item4', 'item5', 'item6',
                    'item7', 'item8', 'item9',
                    'item10'));
```

To also order the corrected item-total correlations, as well as the item-corrected scale means, standard deviations, and reliability coefficients, use:

```r
reliability(dat,
            items=c('item1', 'item2', 'item3',
                    'item4', 'item5', 'item6',
                    'item7', 'item8', 'item9',
                    'item10'),
            itemDiagnostics = TRUE);
```
