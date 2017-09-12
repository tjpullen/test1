---
title       : STAT5
description : 
attachments :


--- type:NormalExercise lang:r xp:100 skills:1 key:509c602d6a
## One sample t test

The **one sample t test** compares the mean of one sample to a particular value.

**Eample: Are our students taller than average?**

The mean height of 19 year-old females in the WHO reference data is 163.1548 cm. You could use a one sample t test to compare a sample of this year's students to this mean value.

*** =instructions

The height of a sample of 20 female students in this age group was measured and placed in the vector `heights`.

Perform a one sample t test to compare the mean of `heights` to the populatio mean (`mu =`) of 163.15.

You need to use the `t.test()` function, and you need to give it the list of all the heights in the sample rather than just the sample mean.

*** =hint
You need to enter 2 arguments: the vector of heights and the population mean: `mu = 163.15`
*** =pre_exercise_code
```{r}
set.seed(967)
heights <- rnorm(n = 20, mean = 163.1548 + 4, sd = 6.5409)

```

*** =sample_code
```{r}
# t test to compare heights to 163.15


```

*** =solution
```{r}
# t test to compare heights to 163.15
t.test(heights, mu = 163.15)

```

*** =sct
```{r}
test_function("t.test", args = c("x", "mu"))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:68cff58e3f
## One sample t test (2)

Perform the t test again to compare `heights` to a population mean of 163.15.

Look at the output.

With a threshold of $\alpha = 0.05$ do you reject the null hypothesis?

*** =instructions
- yes
- no
*** =hint

*** =pre_exercise_code
```{r}
set.seed(967)
heights <- rnorm(n = 20, mean = 163.1548 + 4, sd = 6.5409)
```

*** =sct
```{r}
test_mc(correct = 1)
```

--- type:NormalExercise lang:r xp:100 skills:1 key:04f47ebac9
## Two sample t test

The **two sample t test** compares the means of two samples.

Say you want to test whether a new compound causes overweight mice to lose weight. You could treat 10 mice with the drug and compare them to 10 mice which were not treated with the drug (or better still treated with a placebo drug).

The weights of 10 mice for each cohort have been stored in `data1`. The data are arranged with the weights stored in the `weight` column and a `treatment` column containing either `control` or `drug`.

*** =instructions

First use a box plot to compare the weights grouped by treatment.

Tip: Remember to use the `~` symbol in your formula for the boxplot.
*** =hint
The `~` symbol means, 'is explained by' or 'described by'. So you want to plot `weight` described by `treatment`. You also need to tell boxplot that the data is stored in `data1`.
*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_5357/datasets/STAT5_1.RData"))
```

*** =sample_code
```{r}
# Boxplot of weight grouped by treatment

```

*** =solution
```{r}
# Boxplot of weight grouped by treatment
boxplot(weight ~ treatment, data = data1)

```

*** =sct
```{r}
test_function("boxplot", args = c("formula", "data"))
```




--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:7706d7aba9
## Two sample t test (2)

Take a look at the boxplot.

Does it look like the drug-treated mice have lost weight compared to the control mice?
*** =instructions
- Yes
- No
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_5357/datasets/STAT5_1.RData"))
boxplot(weight ~ treatment, data = data1)
```

*** =sct
```{r}
test_mc(correct = 1)
```
--- type:NormalExercise lang:r xp:100 skills:1 key:1bb567adc1
## Two sample t test (3)

Now you've had a look at the data, you could do a formal hypothesis test.

*** =instructions
Perform a two sample t test to compare the weights grouped by treatment option.

*** =hint
Since you are entering the same data in `t.test()` and `boxplot()` you can use exactly the same formula.
*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_5357/datasets/STAT5_1.RData"))
boxplot(weight ~ treatment, data = data1)
```

*** =sample_code
```{r}
# Boxplot of weight grouped by treatment
boxplot(weight ~ treatment, data = data1)

# t test of weight grouped by treatment


```

*** =solution
```{r}
# Boxplot of weight grouped by treatment
boxplot(weight ~ treatment, data = data1)

# t test of weight grouped by treatment
t.test(weight ~ treatment, data = data1)

```

*** =sct
```{r}
test_function("t.test", args = c("formula", "data"))
```




--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:e70c80f493
## Two sample t test (4)

Repeat the t test you just performed and look at the output.

(t test on `weight` grouped by `treatment` in `data1`)

This time with a threshold of $\alpha = 0.01$ do you reject the null hypothesis?

*** =instructions
- Yes
- No
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_5357/datasets/STAT5_1.RData"))
# boxplot(weight ~ treatment, data = data1)
```

*** =sct
```{r}
test_mc(correct = 2)
```
--- type:PlainMultipleChoiceExercise lang:r xp:50 skills:1 key:71a0c28d63
## One sample t test (3)

With the output `p = 0.04885`, which statement best describes the outcome of this test?

Note: more than one of these statments is correct so choose the one you think most accurately represents the result.
*** =instructions
- This cohort is significantly taller than the WHO reference data
- This result would be unusual if
- There is a 95% probability that this cohort is taller than the reference data
- 
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}

```

