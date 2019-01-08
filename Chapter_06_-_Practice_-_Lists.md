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

## Lists 

Lists, as opposed to vectors, can hold components of different types, just like your to-do list at home or at work. This intro to R chapter will teach you how to create, name and subset these lists.

### Lists, why would you need them?

Congratulations! At this point in the course you are already familiar with:

* **Vectors** (one dimensional array): can hold numeric, character or logical values. The elements in a vector all have the same data type.
* **Matrices** (two dimensional array): can hold numeric, character or logical values. The elements in a matrix all have the same data type.
* **Data frames** (two-dimensional objects): can hold numeric, character or logical values. Within a column all elements have the same data type, but different columns can be of different data type.

Pretty sweet for an R newbie, right?

#### Instructions
*Click 'Submit Answer' to start learning everything about lists!*

```r
# Just click the 'Submit Answer' button.
```
**Ready, set, go! Continue to the next exercise.**

### Lists, why would you need them? (2)

A list in R is similar to your to-do list at work or school: the different items on that list most likely differ in length, characteristic, type of activity that has to do be done...

A list in R allows you to gather a variety of objects under one name (that is, the name of the list) in an ordered way. These objects can be matrices, vectors, data frames, even other lists, etc. It is not even required that these objects are related to each other in any way.

You could say that a list is some kind super data type: you can store practically any piece of information in it!

#### Instructions
*Click 'Submit Answer' to start the first exercise on lists.*

```r
# Click 'Submit Answer' to start the first exercise on lists.
```
**Cool. Let's get our hands dirty!**

### Creating a list

Let us create our first list! To construct a list you use the function `list()`:

    my_list <- list(comp1, comp2 ...)

The arguments to the list function are the list components. Remember, these components can be matrices, vectors, other lists...

#### Instructions
*Construct a list, named* `my_list`*, that contains the variables* `my_vector`*,* `my_matrix` *and* `my_df` *as list components.*

```r
# Vector with numerics from 1 up to 10
my_vector <- 1:10 

# Matrix with numerics from 1 up to 9
my_matrix <- matrix(1:9, ncol = 3)

# First 10 elements of the built-in data frame mtcars
my_df <- mtcars[1:10, ]

# Construct list with these different elements:
my_list <- list(my_vector, my_matrix, my_df)
```
**Wonderful! Head over to the next exercise.**

### Creating a named list

Well done, you're on a roll!

Just like on your to-do list, you want to avoid not knowing or remembering what the components of your list stand for. That is why you should give names to them:

    my_list <- list(name1 = your_comp1, 
                    name2 = your_comp2)

This creates a list with components that are named `name1`, `name2`, and so on. If you want to name your lists after you've created them, you can use the `names()` function as you did with vectors. The following commands are fully equivalent to the assignment above:

    my_list <- list(your_comp1, your_comp2)
    names(my_list) <- c("name1", "name2")

#### Instructions
* *Change the code of the previous exercise (see editor) by adding names to the components. Use for* `my_vector` *the name* `vec`*, for* `my_matrix` *the name* `mat` *and for* `my_df` *the name df.*
* *Print out* `my_list` *so you can inspect the output.*

```r
# Vector with numerics from 1 up to 10
my_vector <- 1:10 

# Matrix with numerics from 1 up to 9
my_matrix <- matrix(1:9, ncol = 3)

# First 10 elements of the built-in data frame mtcars
my_df <- mtcars[1:10,]

# Adapt list() call to give the components names
my_list <- list(my_vector, my_matrix, my_df)
names(my_list) <- c("vec", "mat", "df")

# Print out my_list
my_list
```

```
## $vec
##  [1]  1  2  3  4  5  6  7  8  9 10
## 
## $mat
##      [,1] [,2] [,3]
## [1,]    1    4    7
## [2,]    2    5    8
## [3,]    3    6    9
## 
## $df
##                    mpg cyl  disp  hp drat    wt  qsec vs am gear carb
## Mazda RX4         21.0   6 160.0 110 3.90 2.620 16.46  0  1    4    4
## Mazda RX4 Wag     21.0   6 160.0 110 3.90 2.875 17.02  0  1    4    4
## Datsun 710        22.8   4 108.0  93 3.85 2.320 18.61  1  1    4    1
## Hornet 4 Drive    21.4   6 258.0 110 3.08 3.215 19.44  1  0    3    1
## Hornet Sportabout 18.7   8 360.0 175 3.15 3.440 17.02  0  0    3    2
## Valiant           18.1   6 225.0 105 2.76 3.460 20.22  1  0    3    1
## Duster 360        14.3   8 360.0 245 3.21 3.570 15.84  0  0    3    4
## Merc 240D         24.4   4 146.7  62 3.69 3.190 20.00  1  0    4    2
## Merc 230          22.8   4 140.8  95 3.92 3.150 22.90  1  0    4    2
## Merc 280          19.2   6 167.6 123 3.92 3.440 18.30  1  0    4    4
```
**Great! Not only do you know how to construct lists now, you can also name them; a skill that will prove most useful in practice. Continue to the next exercise.**

### Creating a named list (2)

Being a huge movie fan (remember your job at LucasFilms), you decide to start storing information on good movies with the help of lists.

Start by creating a list for the movie "The Shining". We have already created the variables `mov`, `act` and `rev` in your R workspace. Feel free to check them out in the console.

#### Instructions
*Complete the code on the right to create* `shining_list`*; it contains three elements:*

* *moviename: a character string with the movie title (stored in* `mov`*)*
* *actors: a vector with the main actors' names (stored in* `act`*)*
* *reviews: a data frame that contains some reviews (stored in* `rev`*)*

*Do not forget to name the list components accordingly (names are moviename, actors and reviews).*

```r
# Constructing elements of the future list
scores <- c(4.5, 4.0, 5.0)
sources <- c("IMDB1", "IMDB2", "IMDB3")
comments <- c("Best Horror Film I Have Ever Seen", 
              "A truly brilliant and scary film from Stanley Kubrick", 
              "A masterpiece of psychological horror")

mov <- "The Shining"
act <- c("Jack Nicholson", "Shelley Duvall", "Danny Lloyd", "Scatman Crothers", "Barry Nelson")
rev <- data.frame(scores, sources, comments)

# The variables mov, act and rev are available
mov
```

```
## [1] "The Shining"
```

```r
act
```

```
## [1] "Jack Nicholson"   "Shelley Duvall"   "Danny Lloyd"     
## [4] "Scatman Crothers" "Barry Nelson"
```

```r
rev
```

```
##   scores sources                                              comments
## 1    4.5   IMDB1                     Best Horror Film I Have Ever Seen
## 2    4.0   IMDB2 A truly brilliant and scary film from Stanley Kubrick
## 3    5.0   IMDB3                 A masterpiece of psychological horror
```

```r
# Finish the code to build shining_list
shining_list <- list(moviename = mov, actors = act, reviews = rev)
```
**Wonderful! You now know how to construct and name lists. As in the previous chapters, let's look at how to select elements for lists. Head over to the next exercise.**

### Selecting elements from a list

Your list will often be built out of numerous elements and components. Therefore, getting a single element, multiple elements, or a component out of it is not always straightforward.

One way to select a component is using the numbered position of that component. For example, to "grab" the first component of `shining_list` you type:

    shining_list[[1]]

A quick way to check this out is typing it in the console. Important to remember: to select elements from vectors, you use single square brackets: `[ ]`. Don't mix them up!

You can also refer to the names of the components, with `[[ ]]` or with the `$` sign. Both will select the data frame representing the reviews:

    shining_list[["reviews"]]
    shining_list$reviews

Besides selecting components, you often need to select specific elements out of these components. For example, with `shining_list[[2]][1]` you select from the second component, `actors` (`shining_list[[2]]`), the first element (`[1]`). When you type this in the console, you will see the answer is Jack Nicholson.

#### Instructions
* *Select from* `shining_list` *the vector representing the actors. Simply print out this vector.*
* *Select from* `shining_list` *the second element in the vector representing the actors. Do a printout like before.*

```r
# shining_list, the list containing movie name, actors and reviews, is pre-loaded in the workspace

# Print out the vector representing the actors
shining_list[[2]]
```

```
## [1] "Jack Nicholson"   "Shelley Duvall"   "Danny Lloyd"     
## [4] "Scatman Crothers" "Barry Nelson"
```

```r
shining_list[["actors"]]
```

```
## [1] "Jack Nicholson"   "Shelley Duvall"   "Danny Lloyd"     
## [4] "Scatman Crothers" "Barry Nelson"
```

```r
shining_list$actors
```

```
## [1] "Jack Nicholson"   "Shelley Duvall"   "Danny Lloyd"     
## [4] "Scatman Crothers" "Barry Nelson"
```

```r
# Print the second element of the vector representing the actors
shining_list[["actors"]][2]
```

```
## [1] "Shelley Duvall"
```

```r
shining_list$actors[2]
```

```
## [1] "Shelley Duvall"
```
**Great! Selecting elements from lists is rather easy isn't it? Continue to the next exercise.**

### Adding more movie information to the list

Being proud of your first list, you shared it with the members of your movie hobby club. However, one of the senior members, a guy named M. McDowell, noted that you forgot to add the release year. Given your ambitions to become next year's president of the club, you decide to add this information to the list.

To conveniently add elements to lists you can use the `c()` function, that you also used to build vectors:

    ext_list <- c(my_list , my_val)

This will simply extend the original list, `my_list`, with the component `my_val`. This component gets appended to the end of the list. If you want to give the new list item a name, you just add the name as you did before:

    ext_list <- c(my_list, my_name = my_val)

#### Instructions
* *Complete the code below such that an item named* `year` *is added to the* `shining_list` *with the value 1980. Assign the result to* `shining_list_full`*.*
* *Finally, have a look at the structure of* `shining_list_full` *with the* `str()` *function.*

```r
# shining_list, the list containing movie name, actors and reviews, is pre-loaded in the workspace

# We forgot something; add the year to shining_list
shining_list_full <- c(shining_list, year = 1980)

# Have a look at shining_list_full
str(shining_list_full)
```

```
## List of 4
##  $ moviename: chr "The Shining"
##  $ actors   : chr [1:5] "Jack Nicholson" "Shelley Duvall" "Danny Lloyd" "Scatman Crothers" ...
##  $ reviews  :'data.frame':	3 obs. of  3 variables:
##   ..$ scores  : num [1:3] 4.5 4 5
##   ..$ sources : Factor w/ 3 levels "IMDB1","IMDB2",..: 1 2 3
##   ..$ comments: Factor w/ 3 levels "A masterpiece of psychological horror",..: 3 2 1
##  $ year     : num 1980
```
**Great! This was the last exercise on R lists! You now have a solid basis in the R programming language, but there's so much more to learn. Check out all the other DataCamp courses and become a true data science expert!**
