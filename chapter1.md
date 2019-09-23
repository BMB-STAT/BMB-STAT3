---
title: 'STAT3 - Probability and Risk'
description: 'Understanding uncertainty'
---

## Binomial calculations 1

```yaml
type: NormalExercise
key: 29adcc84b0
lang: r
xp: 100
skills: 1
```

The STAT3 eModule outlines the use of `dbinom`, `pbinom`, and `pnorm`. If you haven't already, complete that eModule first before attempting the following exercises.

Now it's your turn to have a go with these commands and utilising these concepts.

First up, the `dbinom` function.

Remember the `dbinom()` function takes these arguments:
`dbinom(x, size, prob)`

`@instructions`
What is the probability of getting **exactly 3 heads** from 4 coins?

`@hint`


`@pre_exercise_code`
```{r}
barplot(dbinom(0:4, 4, 1/2), names.arg = 0:4, space = 0, col = "grey", xlab = "No of heads", ylab = "Probability", main = "4 coins")
barplot(c(rep(0,3),dbinom(3, 4, 1/2),rep(0,1)), names.arg = 0:4, space = 0, col = "red", add = T)
```

`@sample_code`
```{r}
# The probability of getting 3 heads from 4 coins


```

`@solution`
```{r}
# The probability of getting 3 heads from 4 coins
dbinom(3, size = 4, prob = 0.5)

```

`@sct`
```{r}
test_function("dbinom", args = c("x", "size", "prob"))
```

---

## Binomial calculations 2

```yaml
type: NormalExercise
key: 3821924567
lang: r
xp: 100
skills: 1
```

Now let's try some more medically relevant examples.

`@instructions`
An allergy treatment is known to be 80% effective. 

25 people receive this treatment.

What is the probability that exactly 80% of these patients report no allergy symptoms after treatment?

`@hint`
The outcome could be defined as "report of symptoms" - a "yes" or "no" answer that is appropriate for the binomial distribution model.
80% effective is the same as saying we would expect the allergy treatment to prevent allergy symptoms for 80% of those treated. 
80% of 25 is 20.

`@pre_exercise_code`
```{r}
barplot(dbinom(0:25, 25, 0.8), names.arg = 0:25, space = 0, col = "grey", xlab = "No of patients reporting no symptoms", ylab = "Probability", main = "Allergy Treatment")
barplot(c(rep(0,20),dbinom(20, 25, 0.8),rep(0,5)), names.arg = 0:25, space = 0, col = "red", add = T)
```

`@sample_code`
```{r}
# The probability of 80% of patients reporting no allergy symptoms


```

`@solution`
```{r}
# The probability of 80% of patients reporting no allergy symptoms
dbinom(20, size = 25, prob = 0.8)

```

`@sct`
```{r}
test_function("dbinom", args = c("x", "size", "prob"))
```

---

## Binomial calculations 3

```yaml
type: NormalExercise
key: ca1cd4f3cd
lang: r
xp: 100
skills: 1
```

Here is another example.

`@instructions`
4 out of every 100 people who suffer a heart attack die as a result of that attack.

Suppose we have 15 patients who suffer a heart attack, what is the probability that all will survive?

`@hint`
For this example, we will call a "success" a fatal attack - this might seem weird!
4 out of 100 can be represented as a probability of 0.04. 
We want to know the probability that there are no fatal attacks - i.e. 0 successes.

`@pre_exercise_code`
```{r}
barplot(dbinom(0:15, 15, 0.04), names.arg = 0:15, space = 0, col = "grey", xlab = "No. of fatal heart attacks", ylab = "Probability", main = "Fatality of heart attacks")
barplot(c(dbinom(0, 15, 0.04), rep(0,15)), names.arg = 0:15, space = 0, col = "red", add = T)
```

`@sample_code`
```{r}
# The probability that all 15 heart attack patients survive


```

`@solution`
```{r}
# The probability that all 15 heart attack patients survive
dbinom(0, size = 15, prob = 0.04)

```

`@sct`
```{r}
test_function("dbinom", args = c("x", "size", "prob"))
```

---

## Binomial calculations (2)

```yaml
type: NormalExercise
key: bf295d9c99
lang: r
xp: 100
skills: 1
```

Remember the `pbinom()` function takes the same arguments as `dbinom()`

`@instructions`
What is the probability of getting **up to 3 heads** from 6 coins?
(ie. 0, 1, 2 or 3 heads)

`@hint`


`@pre_exercise_code`
```{r}
barplot(dbinom(0:6, 6, 1/2), names.arg = 0:6, space = 0, col = "grey", xlab = "No of heads", ylab = "Probability", main = "6 coins")
barplot(c(dbinom(0:3, 6, 1/2),rep(0,3)), names.arg = 0:6, space = 0, col = "red", add = T)
```

`@sample_code`
```{r}
# The probability of getting up to 3 heads from 6 coins


```

`@solution`
```{r}
# The probability of getting up to 3 heads from 6 coins
pbinom(3, size = 6, prob = 0.5)

```

`@sct`
```{r}
test_function("pbinom", args = c("q", "size", "prob"))
```

---

## Normal distribution calculations

```yaml
type: NormalExercise
key: 35334c600a
lang: r
xp: 100
skills: 1
```

The `pnorm()` function works just like the `pbinom()` function to calculate the cumulative probability, but of the normal distribution rather than the binomial. It takes the following arguments:

`pnorm(x, mean, sd)`

We've seen the example with 19-year-old males, so let's ask the same question about 19-year-old females with the parameters given below.

`@instructions`
What proportion of 19-year-old females would you expect to be under 170 cm tall?

- Mean = 163.2 cm
- Standard deviation = 6.54

`@hint`


`@pre_exercise_code`
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

`@sample_code`
```{r}
# Proportion of 19-year-old females <170 cm


```

`@solution`
```{r}
# Proportion of 19-year-old females <170 cm
pnorm(170, mean = 163.2, sd = 6.54)

```

`@sct`
```{r}
test_function("pnorm", args = c("q", "mean", "sd"))
```
