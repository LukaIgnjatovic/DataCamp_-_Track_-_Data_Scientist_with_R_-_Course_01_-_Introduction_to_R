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

## Data frames

Most data sets you will be working with will be stored as data frames. By the end of this chapter focused on R basics, you will be able to create a data frame, select interesting parts of a data frame and order a data frame according to certain variables.

### What's a data frame?

You may remember from the chapter about matrices that all the elements that you put in a matrix should be of the same type. Back then, your data set on Star Wars only contained numeric elements.

When doing a market research survey, however, you often have questions such as:

* 'Are your married?' or 'yes/no' questions (`logical`)
* 'How old are you?' (`numeric`)
* 'What is your opinion on this product?' or other 'open-ended' questions (`character`)
* ...

The output, namely the respondents' answers to the questions formulated above, is a data set of different data types. You will often find yourself working with data sets that contain different data types instead of only one.

A data frame has the variables of a data set as columns and the observations as rows. This will be a familiar concept for those coming from different statistical software packages such as SAS or SPSS.

#### Instructions
*Click 'Submit Answer'. The data from the built-in example data frame* `mtcars` *will be printed to the console.*

```r
# Print out built-in R data frame
mtcars
```

```
##                      mpg cyl  disp  hp drat    wt  qsec vs am gear carb
## Mazda RX4           21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
## Mazda RX4 Wag       21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
## Datsun 710          22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
## Hornet 4 Drive      21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1
## Hornet Sportabout   18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
## Valiant             18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
## Duster 360          14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
## Merc 240D           24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
## Merc 230            22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
## Merc 280            19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
## Merc 280C           17.8   6 167.6 123 3.92 3.440 18.90  1  0    4    4
## Merc 450SE          16.4   8 275.8 180 3.07 4.070 17.40  0  0    3    3
## Merc 450SL          17.3   8 275.8 180 3.07 3.730 17.60  0  0    3    3
## Merc 450SLC         15.2   8 275.8 180 3.07 3.780 18.00  0  0    3    3
## Cadillac Fleetwood  10.4   8 472.0 205 2.93 5.250 17.98  0  0    3    4
## Lincoln Continental 10.4   8 460.0 215 3.00 5.424 17.82  0  0    3    4
## Chrysler Imperial   14.7   8 440.0 230 3.23 5.345 17.42  0  0    3    4
## Fiat 128            32.4   4  78.7  66 4.08 2.200 19.47  1  1    4    1
## Honda Civic         30.4   4  75.7  52 4.93 1.615 18.52  1  1    4    2
## Toyota Corolla      33.9   4  71.1  65 4.22 1.835 19.90  1  1    4    1
## Toyota Corona       21.5   4 120.1  97 3.70 2.465 20.01  1  0    3    1
## Dodge Challenger    15.5   8 318.0 150 2.76 3.520 16.87  0  0    3    2
## AMC Javelin         15.2   8 304.0 150 3.15 3.435 17.30  0  0    3    2
## Camaro Z28          13.3   8 350.0 245 3.73 3.840 15.41  0  0    3    4
## Pontiac Firebird    19.2   8 400.0 175 3.08 3.845 17.05  0  0    3    2
## Fiat X1-9           27.3   4  79.0  66 4.08 1.935 18.90  1  1    4    1
## Porsche 914-2       26.0   4 120.3  91 4.43 2.140 16.70  0  1    5    2
## Lotus Europa        30.4   4  95.1 113 3.77 1.513 16.90  1  1    5    2
## Ford Pantera L      15.8   8 351.0 264 4.22 3.170 14.50  0  1    5    4
## Ferrari Dino        19.7   6 145.0 175 3.62 2.770 15.50  0  1    5    6
## Maserati Bora       15.0   8 301.0 335 3.54 3.570 14.60  0  1    5    8
## Volvo 142E          21.4   4 121.0 109 4.11 2.780 18.60  1  1    4    2
```
**Great! Continue to the next exercise.**

### Quick, have a look at your data set

Wow, that is a lot of cars!

Working with large data sets is not uncommon in data analysis. When you work with (extremely) large data sets and data frames, your first task as a data analyst is to develop a clear understanding of its structure and main elements. Therefore, it is often useful to show only a small part of the entire data set.

So how to do this in R? Well, the function `head()` enables you to show the first observations of a data frame. Similarly, the function `tail()` prints out the last observations in your data set.

Both `head()` and `tail()` print a top line called the 'header', which contains the names of the different variables in your data set.

#### Instructions
*Call* `head()` *on the* `mtcars` *data set to have a look at the header and the first observations.*

```r
# Call head() on mtcars
head(mtcars)
```

```
##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb
## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
```
**Wonderful! So, what do we have in this data set? For example,** `hp` **for example represents the car's horsepower; the Datsun has the lowest horse power of the 6 cars that are displayed. For a full overview of the variables' meaning, type** `?mtcars` **in the console and read the help page. Continue to the next exercise!**

### Have a look at the structure

Another method that is often used to get a rapid overview of your data is the function `str()`. The function `str()` shows you the structure of your data set. For a data frame it tells you:

* The total number of observations (e.g. 32 car types)
* The total number of variables (e.g. 11 car features)
* A full list of the variables names (e.g. `mpg`, `cyl`...)
* The data type of each variable (e.g. `num`)
* The first observations

Applying the `str()` function will often be the first thing that you do when receiving a new data set or data frame. It is a great way to get more insight in your data set before diving into the real analysis.

#### Instructions
*Investigate the structure of* `mtcars`*. Make sure that you see the same numbers, variables and data types as mentioned above.*

```r
# Investigate the structure of mtcars
str(mtcars)
```

```
## 'data.frame':	32 obs. of  11 variables:
##  $ mpg : num  21 21 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 ...
##  $ cyl : num  6 6 4 6 8 6 8 4 4 6 ...
##  $ disp: num  160 160 108 258 360 ...
##  $ hp  : num  110 110 93 110 175 105 245 62 95 123 ...
##  $ drat: num  3.9 3.9 3.85 3.08 3.15 2.76 3.21 3.69 3.92 3.92 ...
##  $ wt  : num  2.62 2.88 2.32 3.21 3.44 ...
##  $ qsec: num  16.5 17 18.6 19.4 17 ...
##  $ vs  : num  0 0 1 1 0 1 0 1 1 1 ...
##  $ am  : num  1 1 1 0 0 0 0 0 0 0 ...
##  $ gear: num  4 4 4 3 3 3 3 4 4 4 ...
##  $ carb: num  4 4 1 1 2 1 4 2 2 4 ...
```
**Nice work! Can you find all the information that is listed in the exercise's assignment? Continue to the next exercise.**

### Creating a data frame

Since using built-in data sets is not even half the fun of creating your own data sets, the rest of this chapter is based on your personally developed data set. Put your jet pack on because it is time for some space exploration!

As a first goal, you want to construct a data frame that describes the main characteristics of eight planets in our solar system. According to your good friend Buzz, the main features of a planet are:

* The type of planet (Terrestrial or Gas Giant).
* The planet's diameter relative to the diameter of the Earth.
* The planet's rotation across the sun relative to that of the Earth.
* If the planet has rings or not (TRUE or FALSE).

After doing some high-quality research on Wikipedia, you feel confident enough to create the necessary vectors: `name`, `type`, `diameter`, `rotation` and `rings`; these vectors have already been coded up on the right. The first element in each of these vectors correspond to the first observation.

You construct a data frame with the `data.frame()` function. As arguments, you pass the vectors from before: they will become the different columns of your data frame. Because every column has the same length, the vectors you pass should also have the same length. But don't forget that it is possible (and likely) that they contain different types of data.

#### Instructions
*Use the function* `data.frame()` *to construct a data frame. Pass the vectors* `name`*,* `type`*,* `diameter`*,* `rotation` *and* `rings` *as arguments to* `data.frame()`*, in this order. Call the resulting data frame* `planets_df`*.*

```r
# Definition of vectors
name <- c("Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune")
type <- c("Terrestrial planet", "Terrestrial planet", "Terrestrial planet", 
          "Terrestrial planet", "Gas giant", "Gas giant", "Gas giant", "Gas giant")
diameter <- c(0.382, 0.949, 1, 0.532, 11.209, 9.449, 4.007, 3.883)
rotation <- c(58.64, -243.02, 1, 1.03, 0.41, 0.43, -0.72, 0.67)
rings <- c(FALSE, FALSE, FALSE, FALSE, TRUE, TRUE, TRUE, TRUE)

# Create a data frame from the vectors
planets_df <- data.frame(name, type, diameter, rotation, rings)
```
**Great job! Continue to the next exercise. The logical next step, as you know by now, is inspecting the data frame you just created. Head over to the next exercise.**

### Creating a data frame (2)

The `planets_df` data frame should have 8 observations and 5 variables. It has been made available in the workspace, so you can directly use it.

#### Instructions
*Use* `str()` *to investigate the structure of the new* `planets_df` *variable.*

```r
# Check the structure of planets_df
str(planets_df)
```

```
## 'data.frame':	8 obs. of  5 variables:
##  $ name    : Factor w/ 8 levels "Earth","Jupiter",..: 4 8 1 3 2 6 7 5
##  $ type    : Factor w/ 2 levels "Gas giant","Terrestrial planet": 2 2 2 2 1 1 1 1
##  $ diameter: num  0.382 0.949 1 0.532 11.209 ...
##  $ rotation: num  58.64 -243.02 1 1.03 0.41 ...
##  $ rings   : logi  FALSE FALSE FALSE FALSE TRUE TRUE ...
```
**Awesome! Now that you have a clear understanding of the** `planets_df` **data set, it's time to see how you can select elements from it. Learn all about in the next exercises!**

### Selection of data frame elements

Similar to vectors and matrices, you select elements from a data frame with the help of square brackets `[ ]`. By using a comma, you can indicate what to select from the rows and the columns respectively. For example:

* `my_df[1, 2]` selects the value at the first row and second element in `my_df`.
* `my_df[1:3, 2:4]` selects rows 1, 2, 3 and columns 2, 3, 4 in `my_df`.

Sometimes you want to select all elements of a row or column. For example, `my_df[1, ]` selects all elements of the first row. Let us now apply this technique on `planets_df`!

#### Instructions
* *From* `planets_df`*, select the diameter of Mercury: this is the value at the first row and the third column. Simply print out the result.*
* *From* `planets_df`*, select all data on Mars (the fourth row). Simply print out the result.*

```r
# The planets_df data frame from the previous exercise is pre-loaded

# Print out diameter of Mercury (row 1, column 3)
planets_df[1, 3]
```

```
## [1] 0.382
```

```r
# Print out data for Mars (entire fourth row)
planets_df[4, ]
```

```
##   name               type diameter rotation rings
## 4 Mars Terrestrial planet    0.532     1.03 FALSE
```
**Great! Apart from selecting elements from your data frame by index, you can also use the column names. To learn how, head over to the next exercise.**

### Selection of data frame elements (2)

Instead of using numerics to select elements of a data frame, you can also use the variable names to select columns of a data frame.

Suppose you want to select the first three elements of the `type` column. One way to do this is:

    planets_df[1:3, 1]

A possible disadvantage of this approach is that you have to know (or look up) the column number of `type`, which gets hard if you have a lot of variables. It is often easier to just make use of the variable name:

    planets_df[1:3, "type"]

#### Instructions
*Select and print out the first 5 values in the* `"diameter"` *column of* `planets_df`*.*

```r
# The planets_df data frame from the previous exercise is pre-loaded

# Select first 5 values of diameter column
planets_df[1:5, "diameter"]
```

```
## [1]  0.382  0.949  1.000  0.532 11.209
```
**Nice! Continue to the next exercise!**

### Only planets with rings

You will often want to select an entire column, namely one specific variable from a data frame. If you want to select all elements of the variable `diameter`, for example, both of these will do the trick:

    planets_df[, 3]
    planets_df[, "diameter"]

However, there is a short-cut. If your columns have names, you can use the `$` sign:

    planets_df$diameter

#### Instructions
* *Use the* `$` *sign to select the rings variable from* `planets_df`*. Store the vector that results as* `rings_vector`*.*
* *Print out* `rings_vector` *to see if you got it right.*

```r
# planets_df is pre-loaded in your workspace

# Select the rings variable from planets_df
rings_vector <- planets_df$rings
  
# Print out rings_vector
rings_vector
```

```
## [1] FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE
```
**Great! Continue to the next exercise and discover yet another way of subsetting!**

### Only planets with rings (2)

You probably remember from high school that some planets in our solar system have rings and others do not. But due to other priorities at that time (read: puberty) you can not recall their names, let alone their rotation speed, etc.

Could R help you out?

If you type `rings_vector` in the console, you get:

    [1] FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE

This means that the first four observations (or planets) do not have a ring (`FALSE`), but the other four do (`TRUE`). However, you do not get a nice overview of the names of these planets, their diameter, etc. Let's try to use `rings_vector` to select the data for the four planets with rings.

#### Instructions
*The code on the right selects the* `name` *column of all planets that have rings. Adapt the code so that instead of only the* `name` *column, all columns for planets that have rings are selected.*

```r
# planets_df and rings_vector are pre-loaded in your workspace

# Adapt the code to select all columns for planets with rings
planets_df[rings_vector, ]
```

```
##      name      type diameter rotation rings
## 5 Jupiter Gas giant   11.209     0.41  TRUE
## 6  Saturn Gas giant    9.449     0.43  TRUE
## 7  Uranus Gas giant    4.007    -0.72  TRUE
## 8 Neptune Gas giant    3.883     0.67  TRUE
```
**Wonderful! This is a rather tedious solution. The next exercise will teach you how to do it in a more concise way.**

### Only planets with rings but shorter

So what exactly did you learn in the previous exercises? You selected a subset from a data frame (`planets_df`) based on whether or not a certain condition was true (rings or no rings), and you managed to pull out all relevant data. Pretty awesome! By now, NASA is probably already flirting with your CV).

Now, let us move up one level and use the function `subset()`. You should see the `subset()` function as a short-cut to do exactly the same as what you did in the previous exercises.

    subset(my_df, subset = some_condition)

The first argument of `subset()` specifies the data set for which you want a subset. By adding the second argument, you give R the necessary information and conditions to select the correct subset.

The code below will give the exact same result as you got in the previous exercise, but this time, you didn't need the `rings_vector`!

    subset(planets_df, subset = rings)

#### Instructions
*Use* `subset()` *on* `planets_df` *to select planets that have a diameter smaller than Earth. Because the* `diameter` *variable is a relative measure of the planet's diameter w.r.t that of planet Earth, your condition is* `diameter < 1`*.*

```r
# planets_df is pre-loaded in your workspace

# Select planets with diameter < 1
subset(planets_df, subset = diameter < 1)
```

```
##      name               type diameter rotation rings
## 1 Mercury Terrestrial planet    0.382    58.64 FALSE
## 2   Venus Terrestrial planet    0.949  -243.02 FALSE
## 4    Mars Terrestrial planet    0.532     1.03 FALSE
```
**Great! Not only is the** `subset()` **function more concise, it is probably also more understandable for people who read your code. Continue to the next exercise.**

### Sorting

Making and creating rankings is one of mankind's favorite affairs. These rankings can be useful (best universities in the world), entertaining (most influential movie stars) or pointless (best 007 look-a-like).

In data analysis you can sort your data according to a certain variable in the data set. In R, this is done with the help of the function `order()`.

`order()` is a function that gives you the ranked position of each element when it is applied on a variable, such as a vector for example:

    a <- c(100, 10, 1000)
    order(a)
    [1] 2 1 3

10, which is the second element in `a`, is the smallest element, so 2 comes first in the output of `order(a)`. 100, which is the first element in `a` is the second smallest element, so 1 comes second in the output of `order(a)`.

This means we can use the output of `order(a)` to reshuffle `a`:

    a[order(a)]
    [1]   10  100 1000

#### Instructions
*Experiment with the* `order()` *function in the console. Click 'Submit Answer' when you are ready to continue.*

```r
# Play around with the order function in the console
a <- c(100, 10, 1000)
order(a)
```

```
## [1] 2 1 3
```
**Great! Now let's use the** `order()` **function to sort your data frame!**

### Sorting your data frame

Alright, now that you understand the `order()` function, let us do something useful with it. You would like to rearrange your data frame such that it starts with the smallest planet and ends with the largest one. A sort on the `diameter` column.

#### Instructions
* *Call* `order()` *on* `planets_df$diameter` *(the diameter column of* `planets_df`*). Store the result as* `positions`*.*
* *Now reshuffle* `planets_df` *with the* `positions` *vector as row indexes inside square brackets. Keep all columns. Simply print out the result.*

```r
# planets_df is pre-loaded in your workspace

# Use order() to create positions
positions <- order(planets_df$diameter)

# Use positions to sort planets_df
planets_df[positions, ]
```

```
##      name               type diameter rotation rings
## 1 Mercury Terrestrial planet    0.382    58.64 FALSE
## 4    Mars Terrestrial planet    0.532     1.03 FALSE
## 2   Venus Terrestrial planet    0.949  -243.02 FALSE
## 3   Earth Terrestrial planet    1.000     1.00 FALSE
## 8 Neptune          Gas giant    3.883     0.67  TRUE
## 7  Uranus          Gas giant    4.007    -0.72  TRUE
## 6  Saturn          Gas giant    9.449     0.43  TRUE
## 5 Jupiter          Gas giant   11.209     0.41  TRUE
```
**Wonderful! This exercise concludes the chapter on data frames. Remember that data frames are extremely important in R, you will need them all the time. Another very often used data structure is the list. This will be the subject of the next chapter!**
