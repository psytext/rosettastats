# Recoding a variable

Recoding is the task of changing values of a variable to other values.

## SPSS

```
RECODE x (1=5) (2=4) (3=3) (4=2) (5=1) INTO x_new.
EXECUTE.
```

## R

```
require(car);
dat$x.new <- recode(dat$x, "1=5; 2=4; 3=3; 4=2; 5=1");
```
