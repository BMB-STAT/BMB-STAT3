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

## Binomial calculations 4

```yaml
type: NormalExercise
key: bf295d9c99
lang: r
xp: 100
skills: 1
```

Now lets look at the pbinom function. We use this to calculate the probability of observing up to a certain number of "successes" or events.

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

## Binomial calculations 5

```yaml
type: NormalExercise
key: 3029b4d385
lang: r
xp: 100
skills: 1
```

Now let's return to our heart attack example.

`@instructions`
In a particular hospital, 15 people are admitted with a heart attack.

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

## Binomial calculations 6

```yaml
type: NormalExercise
key: 1ef5730b88
lang: r
xp: 100
skills: 1
```

In the eModule, we looked at the Birthday Problem. 
Although we can't use the pbinom function to solve the Birthday problem, we can use it to answer a slightly different question - what is the probability that *you* share a birthday with someone else in a group of people. We have around 150 students in or STAT class this year - calculate the following probabilities using pbinom:

`@instructions`
- you share your birthday with 1 other person in our STAT class

- you share your birthday with 2 other people in our STAT class

- you share your birthday with 3 other people in our STAT class

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

---

## The Birthday Problem

```yaml
type: MultipleChoiceExercise
key: b401887e8f
xp: 50
```

Although we can't use the dbinom or pbinom function to solve the Birthday problem, we can use these functions to answer a slightly different question - what is the probability that *you* share a birthday with someone else in a group of people. We have around 150 students in or STAT class this year - what is the probability that you share your birthday with one other person in our STAT class?

Remember the `dbinom()` function takes these arguments:
`dbinom(x, size, prob)`

`@possible_answers`
- [0.2719908]
- 0.05588852
- 0.2730661

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- We have around 150 students in our STAT class, but remember, size is the number of trials - you comparing your birthday with 149 other birthdays - therefore size=149
- Your birthday happens on a specific day, therefore the probability of someone sharing that specific day with you is 1/365 - this is the probability argument
- Even though there are 2 of you with the same birthday, the question asks what is the probability that 1 other person shares their birthday with you, therefore there is only 1 success in all your 149 trials  - therefore x = 1

`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
# Check https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises on how to write feedback messages for this exercise.
msg1 <- "This correct, well done!"
msg2 <- "Not quite - remember that even though there are 2 of you with the same birthday, the question asks what is the probability that one other person shares their birthday with you - therefore x = 1"
msg3 <- "Not quite - we have around 150 students in our STAT class, but remember, size is the number of trials - you comparing your birthday with 149 other birthdays - therefore size=149"

ex() %>% check_mc(1, feedback_msgs = c(msg1, msg2, msg3))
```

---

## The Birthday Problem continued

```yaml
type: MultipleChoiceExercise
key: b67d405a70
xp: 50
```

Now calculate the probability that you share your birthday with two other people in our STAT class?

still to be completed!

`@possible_answers`
- [0.2730661]
- 0.05588852
- 0.007574635

`@hint`
<!-- Examples of good hints: https://instructor-support.datacamp.com/en/articles/2379164-hints-best-practices. -->
- you need to use pbinom for this one
- remember that pbinom uses the same arguments as dbinom
- you also need to use the concept of mutual exclusivity - flip the problem around with a '1-'

`@pre_exercise_code`
```{r}

```

`@sct`
```{r}
# Check https://instructor-support.datacamp.com/en/articles/2375523-course-multiple-choice-with-console-exercises on how to write feedback messages for this exercise.
msg1 <- "This correct, well done!"
msg2 <- "Not quite - remember that even though there are 2 of you with the same birthday, the question asks what is the probability that one other person shares their birthday with you - therefore x = 1"
msg3 <- "Not quite - remember that even though there are 2 of you with the same birthday, the question asks what is the probability that one other person shares their birthday with you - therefore x = 1"

ex() %>% check_mc(1, feedback_msgs = c(msg1, msg2, msg3))
```
