---
title: "DataCamp - Introduction to R"
author: "[Luka Ignjatovi&#263;](https://github.com/LukaIgnjatovic)"
output:
  html_document:
    highlight: tango
    theme: united
    toc: yes
    toc_depth: 4
    keep_md: true
  md_document:
    toc: true
    toc_depth: 4
---

## Factors

Very often, data falls into a limited number of categories. For example, humans are either male or female. In R, categorical data is stored in factors. Given the importance of these factors in data analysis, you should start learning how to create, subset and compare them now!

### What's a factor and why would you use it?

In this chapter you dive into the wonderful world of **factors**.

The term factor refers to a statistical data type used to store categorical variables. The difference between a categorical variable and a continuous variable is that a categorical variable can belong to a **limited number of categories**. A continuous variable, on the other hand, can correspond to an infinite number of values.

It is important that R knows whether it is dealing with a continuous or a categorical variable, as the statistical models you will develop in the future treat both types differently. (You will see later why this is the case.)

A good example of a categorical variable is sex. In many circumstances you can limit the sex categories to "Male" or "Female". (Sometimes you may need different categories. For example, you may need to consider chromosomal variation, hermaphroditic animals, or different cultural norms, but you will always have a finite number of categories.)

#### Instructions
*Assign to variable* `theory` *the value* `"factors for categorical variables"`*.*

```r
# Assign to the variable theory what this chapter is about!
theory <- "factors for categorical variables"
```

**Good job! Ready to start? Continue to the next exercise!**

### What's a factor and why would you use it? (2)

To create factors in R, you make use of the function `factor()`. First thing that you have to do is create a vector that contains all the observations that belong to a limited number of categories. For example, `sex_vector` contains the sex of 5 different individuals:

    sex_vector <- c("Male","Female","Female","Male","Male")

It is clear that there are two categories, or in R-terms '**factor levels**', at work here: "Male" and "Female".

The function `factor()` will encode the vector as a factor:

    factor_sex_vector <- factor(sex_vector)

#### Instructions
* *Convert the character vector* `sex_vector` *to a factor with* `factor()` *and assign the result to* `factor_sex_vector`*.*
* *Print out* `factor_sex_vector` *and assert that R prints out the factor levels below the actual values.*

```r
# Sex vector
sex_vector <- c("Male", "Female", "Female", "Male", "Male")

# Convert sex_vector to a factor
factor_sex_vector <- factor(sex_vector)

# Print out factor_sex_vector
factor_sex_vector
```

```
## [1] Male   Female Female Male   Male  
## Levels: Female Male
```

**Great! If you want to find out more about the** `factor()` **function, do not hesitate to type** `?factor` **in the console. This will open up a help page. Continue to the next exercise.**

### What's a factor and why would you use it? (3)

There are two types of categorical variables: a **nominal categorical variable** and an **ordinal categorical variable**.

A nominal variable is a categorical variable without an implied order. This means that it is impossible to say that 'one is worth more than the other'. For example, think of the categorical variable `animals_vector` with the categories: `"Elephant"`, `"Giraffe"`, `"Donkey"` and `"Horse"`. Here, it is impossible to say that one stands above or below the other. (Note that some of you might disagree).

In contrast, ordinal variables do have a natural ordering. Consider for example the categorical variable `temperature_vector` with the categories: `"Low"`, `"Medium"` and `"High"`. Here it is obvious that `"Medium"` stands above `"Low"`, and `"High"` stands above `"Medium"`.

#### Instructions
*Click 'Submit Answer' to check how R constructs and prints nominal and ordinal variables. Do not worry if you do not understand all the code just yet, we will get to that.*

```r
# Animals
animals_vector <- c("Elephant", "Giraffe", "Donkey", "Horse")
factor_animals_vector <- factor(animals_vector)
factor_animals_vector
```

```
## [1] Elephant Giraffe  Donkey   Horse   
## Levels: Donkey Elephant Giraffe Horse
```

```r
# Temperature
temperature_vector <- c("High", "Low", "High","Low", "Medium")
factor_temperature_vector <- factor(temperature_vector, order = TRUE, levels = c("Low", "Medium", "High"))
factor_temperature_vector
```

```
## [1] High   Low    High   Low    Medium
## Levels: Low < Medium < High
```

**Can you already tell what's happening in this exercise? Awesome! Continue to the next exercise and get into the details of factor levels.**

### Factor levels

When you first get a data set, you will often notice that it contains factors with specific factor levels. However, sometimes you will want to change the names of these levels for clarity or other reasons. R allows you to do this with the function `levels()`:

    levels(factor_vector) <- c("name1", "name2",...)

A good illustration is the raw data that is provided to you by a survey. A common question for every questionnaire is the sex of the respondent. Here, for simplicity, just two categories were recorded, `"M"` and `"F"`. (You usually need more categories for survey data; either way, you use a factor to store the categorical data.)

    survey_vector <- c("M", "F", "F", "M", "M")

Recording the sex with the abbreviations `"M"` and `"F"` can be convenient if you are collecting data with pen and paper, but it can introduce confusion when analyzing the data. At that point, you will often want to change the factor levels to `"Male"` and `"Female"` instead of `"M"` and `"F"` for clarity.

**Watch out:** the order with which you assign the levels is important. If you type `levels(factor_survey_vector)`, you'll see that it outputs `[1] "F" "M"`. If you don't specify the levels of the factor when creating the vector, R will automatically assign them alphabetically. To correctly map `"F"` to `"Female"` and `"M"` to `"Male"`, the levels should be set to `c("Female", "Male")`, in this order.

#### Instructions
* *Check out the code that builds a factor vector from* `survey_vector`*. You should use* `factor_survey_vector` *in the next instruction.*
* *Change the factor levels of* `factor_survey_vector` *to* `c("Female", "Male")`*. Mind the order of the vector elements here.*

```r
# Code to build factor_survey_vector
survey_vector <- c("M", "F", "F", "M", "M")
factor_survey_vector <- factor(survey_vector)

# Specify the levels of factor_survey_vector
levels(factor_survey_vector) <- c("Female", "Male")

factor_survey_vector
```

```
## [1] Male   Female Female Male   Male  
## Levels: Female Male
```

**Wonderful! Proceed to the next exercise.**

### Summarizing a factor

After finishing this course, one of your favorite functions in R will be `summary()`. This will give you a quick overview of the contents of a variable:

    summary(my_var)

Going back to our survey, you would like to know how many `"Male"` responses you have in your study, and how many `"Female"` responses. The `summary()` function gives you the answer to this question.

#### Instructions
*Ask a* `summary()` *of the* `survey_vector` *and* `factor_survey_vector`*. Interpret the results of both vectors. Are they both equally useful in this case?*

```r
# Build factor_survey_vector with clean levels
survey_vector <- c("M", "F", "F", "M", "M")
factor_survey_vector <- factor(survey_vector)
levels(factor_survey_vector) <- c("Female", "Male")
factor_survey_vector
```

```
## [1] Male   Female Female Male   Male  
## Levels: Female Male
```

```r
# Generate summary for survey_vector
summary(survey_vector)
```

```
##    Length     Class      Mode 
##         5 character character
```

```r
# Generate summary for factor_survey_vector
summary(factor_survey_vector)
```

```
## Female   Male 
##      2      3
```

**Nice! Have a look at the output. The fact that you identified** `"Male"` **and** `"Female"` **as factor levels in** `factor_survey_vector` **enables R to show the number of elements for each category.**

### Battle of the sexes

In `factor_survey_vector` we have a factor with two levels: Male and Female. But how does R value these relatively to each other? In other words, who does R think is better, males or females?

#### Instructions
*Read the code in the editor and click 'Submit Answer' to see whether males are worth more than females.*

```r
# Build factor_survey_vector with clean levels
survey_vector <- c("M", "F", "F", "M", "M")
factor_survey_vector <- factor(survey_vector)
levels(factor_survey_vector) <- c("Female", "Male")

# Male
male <- factor_survey_vector[1]

# Female
female <- factor_survey_vector[2]

# Battle of the sexes: Male 'larger' than female?
male > female
```

```
## Warning in Ops.factor(male, female): '>' not meaningful for factors
```

```
## [1] NA
```

**How interesting! By default, R returns** `NA` **when you try to compare values in a factor, since the idea doesn't make sense. Next you'll learn about ordered factors, where more meaningful comparisons are possible.**

### Ordered factors

Since `"Male"` and `"Female"` are unordered (or nominal) factor levels, R returns a warning message, telling you that the greater than operator is not meaningful. As seen before, R attaches an equal value to the levels for such factors.

But this is not always the case! Sometimes you will also deal with factors that do have a natural ordering between its categories. If this is the case, we have to make sure that we pass this information to R...

Let us say that you are leading a research team of five data analysts and that you want to evaluate their performance. To do this, you track their speed, evaluate each analyst as `"slow"`, `"medium"` or `"fast"`, and save the results in `speed_vector`.

#### Instructions
*As a first step, assign* `speed_vector` *a vector with 5 entries, one for each analyst. Each entry should be either* `"slow"`*,* `"medium"`*, or* `"fast"`*. Use the list below:*

* *Analyst 1 is medium,*
* *Analyst 2 is slow,*
* *Analyst 3 is slow,*
* *Analyst 4 is medium and*
* *Analyst 5 is fast.*

*No need to specify these are factors yet.*

```r
# Create speed_vector
speed_vector <- c("medium", "slow", "slow", "medium", "fast")
```

**A job well done! Continue to the next exercise.**

### Ordered factors (2)

`speed_vector` should be converted to an ordinal factor since its categories have a natural ordering. By default, the function `factor()` transforms `speed_vector` into an unordered factor. To create an ordered factor, you have to add two additional arguments: `ordered` and `levels`.

    factor(some_vector,
          ordered = TRUE,
          levels = c("lev1", "lev2" ...))

By setting the argument `ordered` to `TRUE` in the function `factor()`, you indicate that the factor is ordered. With the argument `levels` you give the values of the factor in the correct order.

#### Instructions
*From* `speed_vector`*, create an ordered factor vector:* `factor_speed_vector`*. Set* `ordered` *to* `TRUE`*, and set* `levels` *to* `c("slow", "medium", "fast")`*.*

```r
# Create speed_vector
speed_vector <- c("medium", "slow", "slow", "medium", "fast")

# Convert speed_vector to ordered factor vector
factor_speed_vector <- factor(speed_vector, 
                              ordered = TRUE, 
                              levels = c("slow", "medium", "fast"))

# Print factor_speed_vector
factor_speed_vector
```

```
## [1] medium slow   slow   medium fast  
## Levels: slow < medium < fast
```

```r
summary(factor_speed_vector)
```

```
##   slow medium   fast 
##      2      2      1
```

**Great! Have a look at the console. It is now indicated that the levels indeed have an order associated, with the** `<` **sign. Continue to the next exercise.**

### Comparing ordered factors

Having a bad day at work, 'data analyst number two' enters your office and starts complaining that 'data analyst number five' is slowing down the entire project. Since you know that 'data analyst number two' has the reputation of being a smarty-pants, you first decide to check if his statement is true.

The fact that `factor_speed_vector` is now ordered enables us to compare different elements (the data analysts in this case). You can simply do this by using the well-known operators.

#### Instructions
* *Use* `[2]` *to select from* `factor_speed_vector` *the factor value for the second data analyst. Store it as* `da2`*.*
* *Use* `[5]` *to select the* `factor_speed_vector` *factor value for the fifth data analyst. Store it as* `da5`*.*
* *Check if* `da2` *is greater than* `da5`*; simply print out the result. Remember that you can use the* `>` *operator to check whether one element is larger than the other.*

```r
# Create factor_speed_vector
speed_vector <- c("medium", "slow", "slow", "medium", "fast")
factor_speed_vector <- factor(speed_vector, ordered = TRUE, levels = c("slow", "medium", "fast"))

# Factor value for second data analyst
da2 <- factor_speed_vector[2]

# Factor value for fifth data analyst
da5 <- factor_speed_vector[5]

# Is data analyst 2 faster than data analyst 5?
da2 > da5
```

```
## [1] FALSE
```

**Bellissimo! What do the result tell you? Data analyst two is complaining about the data analyst five while in fact he or she is the one slowing everything down! This concludes the chapter on factors. With a solid basis in vectors, matrices and factors, you're ready to dive into the wonderful world of data frames, a very important data structure in R!**
