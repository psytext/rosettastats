# Loading data from a file

In this example, the data will be stored in a file called `mydata.csv` on the desktop of a user called `example` on a PC running the Windows 10 Operating System, and once loaded, the dataset/dataframe will be called `dat`. In all these examples, forward slashes will be used because these are platform-independent and have no special meaning (unlike the backslash, which is used, for example, as escape character in R).

## SPSS

```
GET DATA
  /FILE = 'C:/Users/example/Desktop/mydata.csv'.
DATASET NAME dat.
DATASET ACTIVATE dat.
```

## R

```r
dat <- getData('C:/Users/example/Desktop/mydata.csv');
```
