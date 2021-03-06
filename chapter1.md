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

Since it looks like there's an effect, let's do a formal hypothesis test to quantify this.

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



--- type:NormalExercise lang:r xp:100 skills:1 key:028ac3286c
## Dealing with variation between replicates

Statistics can be used to distinguish an effect which is masked by random variation - in other words, to detect a signal over the background noise.

The dataframe `data2`, contains the results of an siRNA knockdown experiment. In this experiment, a cell line was transfected with either an siRNA targetting a gene of interest (gene A) or control siRNA. The expression level of gene B was measured and is in the `output` column. 6 replicates were performed on different days. Take a look at the data to see if knocking down gene A has an effect on the expression level of gene B.

*** =instructions
Plot a boxplot for the `output` column grouped by `treatment` for the data in `data2`.
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_5357/datasets/STAT5_2.RData"))
```

*** =sample_code
```{r}
# Boxplot of output grouped by treatment

```

*** =solution
```{r}
# Boxplot of output grouped by day
boxplot(output ~ treatment, data = data2)

```

*** =sct
```{r}
test_function("boxplot", args = c("formula", "data"))
```



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:4fb9825166
## Dealing with variation between replicates (2)

Take a look at the boxplot you just plotted.

Does it look like the siRNA has an effect on expression of gene B?

*** =instructions
- Yes, a large effect
- Yes, a small but clear effect
- Possibly, a small effect
- No, no clear effect
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_5357/datasets/STAT5_2.RData"))
boxplot(output ~ treatment, data = data2)
```

*** =sct
```{r}
test_mc(correct = 3)
```



--- type:NormalExercise lang:r xp:100 skills:1 key:c1998ab6d2
## Dealing with variation between replicates (3)

It looks like there may be an effect, but the effect is small relative to the dispersion of the data.

Perform a two sample t test to determine the likelihood of observing a result like this if there were no effect.
*** =instructions
Perform a two sample t test on `output` grouped by `treatment` from `data2`.

Look at the output, and note down the *p value*.
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_5357/datasets/STAT5_2.RData"))
```

*** =sample_code
```{r}
# t test on output grouped by treatment

```

*** =solution
```{r}
# t test on output grouped by treatment
t.test(output ~ treatment, data = data2)

```

*** =sct
```{r}
test_function("t.test", args = c("formula", "data"))
```


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:acf3acd269
## Dealing with variation between replicates (4)

With $\alpha = 0.05$ do you reject the null hypothesis?
*** =instructions
- Yes
- No
*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}
test_mc(correct = 2)
```

--- type:NormalExercise lang:r xp:100 skills:1 key:77c5375f09
## Looking at the data more closely

You failed to reject the null hypothsis, but let's take a closer look at the data.

The trouble with boxplots is that they don't show the individual data points. By looking at the raw data, you may see a pattern that isn't apparent from summary statistics.

You can use the `plot()` function to plot individual data points grouped by `day` to see how much variation there was between replicates. However, if the grouping variable is a factor, R will produce a box plot. If you tell it to treat `day` as a numeric variable using `as.numeric(day)`, it will plot a scatter plot.

*** =instructions
Plot a scatter plot of `output` grouped by `day` from `data2`
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_5357/datasets/STAT5_2.RData"))
```

*** =sample_code
```{r}
# Scatter plot of output grouped by day

```

*** =solution
```{r}
# Scatter plot of output grouped by day
plot(output ~ as.numeric(day), data = data2)
```

*** =sct
```{r}
test_function("plot", args = c("formula", "data"))
```



--- type:NormalExercise lang:r xp:100 skills:1 key:660cefb3bd
## Looking at the data (even) more closely

That's great, but it would be helpful to know which datapoint refers to which treatment.

You can easily do this by colouring the data points with the `col =` argument.


*** =instructions
Add in the `col = ` argument to colour the datapoints by `treatment`.
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_5357/datasets/STAT5_2.RData"))
```

*** =sample_code
```{r}
# Scatter plot of output grouped by day and coloured by treatment
plot(output ~ as.numeric(day), data = data2)
```

*** =solution
```{r}
# Scatter plot of output grouped by day and coloured by treatment
plot(output ~ as.numeric(day), data = data2, col = treatment)

```

*** =sct
```{r}
test_function('plot', args = c('formula', 'data', 'col'))
```



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:dee54eda39
## Dealing with variation between replicates (5)

Look at the scatter plot and interpret what the data shows.

Note: Black = control and Red = siRNA

*** =instructions
- 
*** =hint

*** =pre_exercise_code
```{r}
load(url("http://s3.amazonaws.com/assets.datacamp.com/production/course_5357/datasets/STAT5_2.RData"))
# Scatter plot of output grouped by day and coloured by treatment
plot(output ~ as.numeric(day), data = data2, col = treatment)
```

*** =sct
```{r}

```


--- type:NormalExercise lang:r xp:100 skills:1 key:1dd88f988a
## Paired t test (4)




*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

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
--- type:VideoExercise lang:r xp:50 skills:1 key:7bc75b2e79
## How does the t test work?


*** =video_link
//player.vimeo.com/video/154783078



--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:1a4c22d00a
## Assumptions of the t test (1)



*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}

```


--- type:NormalExercise lang:r xp:100 skills:1 key:cd73744d94
## Assumptions of the t test (2)




*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

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

--- type:NormalExercise lang:r xp:100 skills:1 key:e1591a53fc
## Assumptions of the t test (3)



*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

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


--- type:VideoExercise lang:r xp:50 skills:1 key:ceda018afc
## Statistical power


*** =video_link
//player.vimeo.com/video/154783078


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:c166f5d1c6
## Statistical power (2)



*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}

```


--- type:NormalExercise lang:r xp:100 skills:1 key:731ff43525
## Statistical power (3)

** Content not found **


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

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

--- type:VideoExercise lang:r xp:50 skills:1 key:ddbb4c08fe
## The problem with multiple testing


*** =video_link
//player.vimeo.com/video/154783078


--- type:MultipleChoiceExercise lang:r xp:50 skills:1 key:bd50d77fba
## Multiple testing (2)


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sct
```{r}

```


--- type:NormalExercise lang:r xp:100 skills:1 key:5d5572f407
## Multiple testing 2




*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

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


--- type:NormalExercise lang:r xp:100 skills:1 key:10f7d807d3
## Multiple testing (3)




*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

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
