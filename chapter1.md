---
title       : STAT5
description : 
attachments :





--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:8166ff1177
## One sample t test

The **one sample t test** compares the mean of one sample to a fixed value.

**Eample: Are our students taller than average?**

The WHO 2007 reference height for 19 year-old females has a mean of 163.1548 cm. The height of a sample of 20 female students in this age group has been measured and placed in the vector `heights`. You could use a one sample t test to compare the sample mean for this cohort to the population mean given by the WHO.

Firstly, what is the mean of `heights`?

*** =instructions
- 163.1
- 163.2
- 164.2
- 164.8
- 165.6

*** =hint
You could use either the `mean()` or `summary()` function to gain this information.

*** =pre_exercise_code
```{r}
set.seed(967)
heights <- rnorm(n = 20, mean = 163.1548 + 4, sd = 6.5409)
```

*** =sct
```{r}
test_mc(correct = 5)
```
--- type:NormalExercise lang:r xp:100 skills:1 key:509c602d6a
## One sample t test (2)

The sample mean is 165.6 which is of course higher than the population mean of 163.15. However, this small sample may not be representative of the cohort. The t test allows you to determine how unlikely it is that you get a result this extreme (or more extreme) if the cohort of students had the same mean as the WHO reference data.

*** =instructions

Perform a one sample t test to compare the mean of `heights` to the populatio mean (mu) of 163.15.

You need to use the `t.test()` function, and you need to give it the list of all the heights in the sample rather than just the sample mean.

*** =hint
You need to enter 2 arguments: the vector of heights and the population mean: `mu = `
*** =pre_exercise_code
```{r}
set.seed(967)
heights <- rnorm(n = 20, mean = 163.1548 + 4, sd = 6.5409)

```

*** =sample_code
```{r}
# Mean of heights
mean(heights)

# t test to compare heights to 163.15


```

*** =solution
```{r}
# Mean of heights
mean(heights)

# t test to compare heights to 163.15
t.test(heights, mu = 163.15)

```

*** =sct
```{r}
test_function("t.test", args = c("x", "mu"))
```
