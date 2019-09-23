---
title       : STAT3 - Probability and Risk
description : Understanding uncertainty

--- type:NormalExercise lang:r xp:100 skills:1 key:29adcc84b0
## Binomial calculations

Now it's your turn to have a go.

Remember the `dbinom()` function takes these arguments:
`dbinom(x, size, prob)`

*** =instructions
What is the probability of getting **exactly 3 heads** from 4 coins?
*** =hint

*** =pre_exercise_code
```{r}
barplot(dbinom(0:4, 4, 1/2), names.arg = 0:4, space = 0, col = "grey", xlab = "No of heads", ylab = "Probability", main = "4 coins")
barplot(c(rep(0,3),dbinom(3, 4, 1/2),rep(0,1)), names.arg = 0:4, space = 0, col = "red", add = T)
```

*** =sample_code
```{r}
# The probability of getting 3 heads from 4 coins


```

*** =solution
```{r}
# The probability of getting 3 heads from 4 coins
dbinom(3, size = 4, prob = 0.5)

```

*** =sct
```{r}
test_function("dbinom", args = c("x", "size", "prob"))
```

--- type:NormalExercise lang:r xp:100 skills:1 key:bf295d9c99
## Binomial calculations (2)

Now it's your turn to have a go.

Remember the `pbinom()` function takes the same arguments as `dbinom()`

*** =instructions
What is the probability of getting **up to 3 heads** from 6 coins?
(ie. 0, 1, 2 or 3 heads)
*** =hint

*** =pre_exercise_code
```{r}
barplot(dbinom(0:6, 6, 1/2), names.arg = 0:6, space = 0, col = "grey", xlab = "No of heads", ylab = "Probability", main = "6 coins")
barplot(c(dbinom(0:3, 6, 1/2),rep(0,3)), names.arg = 0:6, space = 0, col = "red", add = T)
```

*** =sample_code
```{r}
# The probability of getting up to 3 heads from 6 coins


```

*** =solution
```{r}
# The probability of getting up to 3 heads from 6 coins
pbinom(3, size = 6, prob = 0.5)

```

*** =sct
```{r}
test_function("pbinom", args = c("q", "size", "prob"))
```

--- type:NormalExercise lang:r xp:100 skills:1 key:35334c600a
## Normal distribution calculations

The `pnorm()` function works just like the `pbinom()` function to calculate the cumulative probability, but of the normal distribution rather than the binomial. It takes the following arguments:

`pnorm(x, mean, sd)`

We've seen the example with 19-year-old males, so let's ask the same question about 19-year-old females with the parameters given below.

*** =instructions
What proportion of 19-year-old females would you expect to be under 170 cm tall?

- Mean = 163.2 cm
- Standard deviation = 6.54

*** =hint

*** =pre_exercise_code
```{r}
mean = 163.2
sd = 6.54
lb = 130
ub = 170
x <- seq(130, 200, length.out = 1000)
hx <- dnorm(x, mean = mean, sd = sd)
plot(x, hx, type = "n", xlab = "Height (cm)", ylab = "Probability", main = "Female Height at 19 years")
i <- x >= lb & x <= ub
lines(x, hx)
polygon(c(min(x[i]), x[i], max(x[i])), c(0, hx[i], 0), col = "red")
```

*** =sample_code
```{r}
# Proportion of 19-year-old females <170 cm


```

*** =solution
```{r}
# Proportion of 19-year-old females <170 cm
pnorm(170, mean = 163.2, sd = 6.54)

```

*** =sct
```{r}
test_function("pnorm", args = c("q", "mean", "sd"))
```

