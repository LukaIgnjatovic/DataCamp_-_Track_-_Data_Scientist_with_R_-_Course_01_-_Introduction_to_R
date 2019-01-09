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

## Intro to basics

In this chapter, you will take your first steps with R. You will learn how to use the console as a calculator and how to assign variables. You will also get to know the basic data types in R. Let's get started!

### How it works

In the editor on the right you should type R code to solve the exercises. When you hit the 'Submit Answer' button, every line of code is interpreted and executed by R and you get a message whether or not your code was correct. The output of your R code is shown in the console in the lower right corner.

R makes use of the `#` sign to add comments, so that you and others can understand what the R code is about. Just like Twitter! Comments are not run as R code, so they will not influence your result. For example, *Calculate 3 + 4* in the editor on the right is a comment.

You can also execute R commands straight in the console. This is a good way to experiment with R code, as your submission is not checked for correctness.

#### Instructions
* *In the editor on the right there is already some sample code. Can you see which lines are actual R code and which are comments?*
* *Add a line of code that calculates the sum of 6 and 12, and hit the 'Submit Answer' button.*

```r
# Calculate 3 + 4
3 + 4
```

```
## [1] 7
```

```r
# Calculate 6 + 12
6 + 12
```

```
## [1] 18
```

**Awesome! See how the console shows the result of the R code you submitted? Now that you're familiar with the interface, let's get down to R business!**

### Arithmetic with R

In its most basic form, R can be used as a simple calculator. Consider the following arithmetic operators:

* Addition: **`+`**
* Subtraction: **`-`**
* Multiplication: **`*`**
* Division: **`/`**
* Exponentiation: **`^`**
* Modulo: **`%%`**

The last two might need some explaining:

* The `^` operator raises the number to its left to the power of the number to its right: for example `3^2` is 9.
* The modulo returns the remainder of the division of the number to the left by the number on its right, for example 5 modulo 3 or `5 %% 3` is 2.

With this knowledge, follow the instructions below to complete the exercise.

#### Instructions
* *Type* `2^5` *in the editor to calculate 2 to the power 5.*
* *Type* `28 %% 6` *to calculate 28 modulo 6.*
* *Click 'Submit Answer' and have a look at the R output in the console.*
* *Note how the* `#` *symbol is used to add comments on the R code.*

```r
# An addition
5 + 5 
```

```
## [1] 10
```

```r
# A subtraction
5 - 5 
```

```
## [1] 0
```

```r
# A multiplication
3 * 5
```

```
## [1] 15
```

```r
# A division
(5 + 5) / 2 
```

```
## [1] 5
```

```r
# Exponentiation
2 ^ 5
```

```
## [1] 32
```

```r
# Modulo
28 %% 6
```

```
## [1] 4
```

**Great! Head over to the next exercise.**

### Variable assignment

A basic concept in (statistical) programming is called a **variable**.

A variable allows you to store a value (e.g. 4) or an object (e.g. a function description) in R. You can then later use this variable's name to easily access the value or the object that is stored within this variable.

You can assign a value 4 to a variable `my_var` with the command:

    my_var <- 4

#### Instructions
*Over to you: complete the code in the editor such that it assigns the value 42 to the variable* `x` *in the editor. Click 'Submit Answer'. Notice that when you ask R to print* `x`*, the value 42 appears.*

```r
# Assign the value 42 to x
x <- 42

# Print out the value of the variable x
x
```

```
## [1] 42
```

**Good job! Have you noticed that R does not print the value of a variable to the console when you did the assignment?** `x <- 42` **did not generate any output, because R assumes that you will be needing this variable in the future. Otherwise you wouldn't have stored the value in a variable in the first place, right? Proceed to the next exercise!**

### Variable assignment (2)

Suppose you have a fruit basket with five apples. As a data analyst in training, you want to store the number of apples in a variable with the name `my_apples`.

#### Instructions
* *Type the following code in the editor:* `my_apples <- 5`*. This will assign the value 5 to* `my_apples`*.*
* *Type:* `my_apples` *below the second comment. This will print out the value of* `my_apples`*.*
* *Click 'Submit Answer', and look at the console: you see that the number 5 is printed. So R now links the variable* `my_apples` *to the value 5.*

```r
# Assign the value 5 to the variable my_apples
my_apples <- 5

# Print out the value of the variable my_apples
my_apples
```

```
## [1] 5
```

**Great! Continue to the next exercise!**

### Variable assignment (3)

Every tasty fruit basket needs oranges, so you decide to add six oranges. As a data analyst, your reflex is to immediately create the variable `my_oranges` and assign the value 6 to it. Next, you want to calculate how many pieces of fruit you have in total. Since you have given meaningful names to these values, you can now code this in a clear way:

    my_apples + my_oranges

#### Instructions
* *Assign to* `my_oranges` *the value 6.*
* *Add the variables* `my_apples` *and* `my_oranges` *and have R simply print the result.*
* *Assign the result of adding* `my_apples` *and* `my_oranges` *to a new variable* `my_fruit`*.*

```r
# Assign a value to the variables my_apples and my_oranges
my_apples <- 5
my_oranges <- 6

# Add these two variables together
my_apples + my_oranges
```

```
## [1] 11
```

```r
# Create the variable my_fruit
my_fruit <- my_apples + my_oranges
```

**Nice one! The great advantage of doing calculations with variables is reusability. If you just change** `my_apples` **to equal 12 instead of 5 and rerun the script,** `my_fruit` **will automatically update as well. Continue to the next exercise.**

### Apples and oranges

Common knowledge tells you not to add apples and oranges. But hey, that is what you just did, no? The `my_apples` and `my_oranges` variables both contained a number in the previous exercise. The `+` operator works with numeric variables in R. If you really tried to add "apples" and "oranges", and assigned a text value to the variable `my_oranges` (see the editor), you would be trying to assign the addition of a numeric and a character variable to the variable `my_fruit`. This is not possible.

#### Instructions
* *Click 'Submit Answer' and read the error message. Make sure to understand why this did not work.*
* *Adjust the code so that R knows you have 6 oranges and thus a fruit basket with 11 pieces of fruit.*

```r
# Assign a value to the variable my_apples
my_apples <- 5 

# Fix the assignment of my_oranges
my_oranges <- "six"
my_oranges <- 6

# Create the variable my_fruit and print it out
my_fruit <- my_apples + my_oranges 
my_fruit
```

```
## [1] 11
```

**Awesome, keep up the good work! Continue to the next exercise.**

### Basic data types in R

R works with numerous data types. Some of the most basic types to get started are:

* Decimals values like `4.5` are called **numerics**.
* Natural numbers like `4` are called **integers**. Integers are also numerics.
* Boolean values (`TRUE` or `FALSE`) are called **logical**.
* Text (or string) values are called **characters**.

Note how the quotation marks on the right indicate that "some text" is a character.

#### Instructions
*Change the value of the:*

* `my_numeric` *variable to* `42`*.*
* `my_character` *variable to* `"universe"`*. Note that the quotation marks indicate that* `"universe"` *is a character.*
* `my_logical` *variable to* `FALSE`*.*

*Note that R is case sensitive!*

```r
# Change my_numeric to be 42
my_numeric <- 42

# Change my_character to be "universe"
my_character <- "universe"

# Change my_logical to be FALSE
my_logical <- FALSE
```

**Great work! Continue to the next exercise.**

### What's that data type?

Do you remember that when you added `5 + "six"`, you got an error due to a mismatch in data types? You can avoid such embarrassing situations by checking the data type of a variable beforehand. You can do this with the `class()` function, as the code on the right shows.

#### Instructions
*Complete the code in the editor and also print out the classes of* `my_character` *and* `my_logical`*.*

```r
# Declare variables of different types
my_numeric <- 42
my_character <- "universe"
my_logical <- FALSE 

# Check class of my_numeric
class(my_numeric)
```

```
## [1] "numeric"
```

```r
# Check class of my_character
class(my_character)
```

```
## [1] "character"
```

```r
# Check class of my_logical
class(my_logical)
```

```
## [1] "logical"
```

**Congratulations! This was the last exercise for this chapter. Head over to the next chapter to get immersed in the world of vectors!**
