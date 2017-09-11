---
title       : STAT5
description : 
attachments :





--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:8166ff1177
## One sample t test

The **one sample t test** compares the mean of one sample to a fixed value.

**Are our students taller than average?**

For example, the WHO 2007 reference height for 19 year-old females has a mean of 163.1548 cm. If you measured the height of a sample of 20 female students in this age group, you could test whether our cohort was taller than the population average.

The heights of a sample of 20 female students has been measured and placed in the vector `heights`.

- Find the mean height.

*** =instructions
- 163.1
- 163.2
- 164.2
- 164.8
- 165.6

*** =hint

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
## One sample t test

The **one sample t test** compares the mean of one sample to a fixed value.

**Are our students taller than average?**

For example, the WHO 2007 reference height for 19 year-old females has a mean of 163.1548 cm. If you measured the height of a sample of 20 female students in this age group, you could test whether our cohort was taller than the population average.



*** =instructions
The heights of a sample of 20 female students has been measured and placed in the vector `heights`.

- Find the mean height.

*** =hint
You could use either the `mean()` or `summary()` function to gain this information.
*** =pre_exercise_code
```{r}
set.seed(967)
heights <- rnorm(n = 20, mean = 163.1548 + 4, sd = 6.5409)

```

*** =sample_code
```{r}

```

*** =solution
```{r}

```

*** =sct
```{r}

```
