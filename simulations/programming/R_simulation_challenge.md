## Advanced R

*(Don't worry if this section of the guide takes awhile -- it's definitely the longest part!)*

1.) Quickly skim these chapters (without doing the exercises) to make sure you're familiar with the concepts:

 * ["Data Structures"](http://adv-r.had.co.nz/Data-structures.html)
 * ["Subsetting"](http://adv-r.had.co.nz/Subsetting.html)

2.) Read about Debugging, an important skill:

 * Read [What to do if you are stuck](https://github.com/avantcredit/avant-analytics/wiki/What-to-do-if-you're-stuck).
 * Read ["Debugging"](http://adv-r.had.co.nz/Exceptions-Debugging.html) from Advanced R, but don't do the exercises.
 * Read about [bettertrace](https://github.com/robertzk/bettertrace). 

3.) Hadley co-authored ["R for Data Science"](http://r4ds.had.co.nz/).  Read these two chapters and do all the exercises in them:

 * ["Data Transformation"](http://r4ds.had.co.nz/transform.html)
 * ["Functions 101"](http://r4ds.had.co.nz/functions.html)

4.) Read the following chapters of "Advanced R":

 * ["Functions 102"](http://adv-r.had.co.nz/Functions.html). Do the three exercises in the "Lexical scoping" section (the ones right after the "Dynamic lookup" subsection) and then go back and do the beginning quiz.
 * ["Functional Programming"](http://adv-r.had.co.nz/Functional-programming.html) Don't do any exercises. 
 * ["Functionals"](http://adv-r.had.co.nz/Functionals.html). Do the first five exericses, but the rest are optional.
 * ["Function Operators"](http://adv-r.had.co.nz/Function-operators.html) and do all the exercises.
 * ["Non-standard evaluation"](http://adv-r.had.co.nz/Computing-on-the-language.html), exercises are optional.
 * ["Performance"](http://adv-r.had.co.nz/Performance.html) but don't do the exercises.
 * ["Profiling"](http://adv-r.had.co.nz/Profiling.html) but don't do the exercises.
 * ["Memory"](http://adv-r.had.co.nz/memory.html) but don't do the exercises.

*(Exercises will go in your answers folder in a separate file. Make a PR when you've finished all these exercises.)*

5.) Read on magrittr (`%>%`) [here](https://github.com/smbache/magrittr/blob/master/README.md) and [here](https://github.com/smbache/magrittr/blob/master/vignettes/magrittr.Rmd).

6.) Make a function that takes another function and returns a function that will print all the arguments and then run the orginal function.

```R
add <- function(x, y) x + y
fn <- arg_printer(add)
fn(2, 3)
[1] "I was called with 2 and 3."
[1] 5
```

7.) Make a function `errors_are_nas` that takes an expression and returns an `NA` if that expression fails instead of an error.

8.) **Optional** These chapters in "R for Data Science" are useful, but not mandatory for our work:

* ["Visualization"](http://r4ds.had.co.nz/data-visualisation.html) - Good way to learn about ggplot2!
* ["Transform"](http://r4ds.had.co.nz/transform.html) - Good way to learn about dplyr!
* ["Tidy data"](http://r4ds.had.co.nz/tidy-data.html) - While all data at Avant is already tidy, it's good to understand the "tidy data" philosophy.

9.) **Optional** Read on [R6 classes](https://cran.r-project.org/web/packages/R6/vignettes/Introduction.html). Try constructing a bank account class with deposit, check balance, and withdraw methods.
