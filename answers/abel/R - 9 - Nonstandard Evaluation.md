**Nonstandard Evaluation: Capture Expressions**

1. One important feature of deparse() to be aware of when programming is that it can return multiple strings if the input is too long. For example, the following call produces a vector of length two:

g(a + b + c + d + e + f + g + h + i + j + k + l + m + n + o + p + q + r + s + t + u + v + w + x + y + z)
Why does this happen? Carefully read the documentation for ?deparse. Can you write a wrapper around deparse() so that it always returns a single string?

```
trim_and_concatenate <- function(e1, e2) {paste(e1, substring(e2, first = 5)) }

one_string_g <- function(x) {
  x %>% substitute %>% deparse %>% Reduce(trim_and_concatenate, . )
}
```

# could instead do x %>% g %>% Reduce(trim_and_concatenate, . ), if g defined earlier


2. Why does as.Date.default() use substitute() and deparse()? Why does pairwise.t.test() use them? Read the source code.

 as.Date.default() uses substitute() and deparse() to create an informative error message.

 pairwise.t.test() creates an output object that remembers how the first two objects were passed to the function:
 x <- 1:5
 y <- 101:105
 z <- pairwise.t.test(x,y)
 z$data.name
 # "x and y"


3. pairwise.t.test() assumes that deparse() always returns a length one character vector. Can you construct an input that violates this expectation? What happens?

you need an input that forces deparse(substitute(.)) to return a length 2 vector. From Peter's solutions,

`pairwise.t.test(
  c(1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1),
  c(1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1)
)`

will do it. The function will exectute, but the output object will be corrupted.




4. f(), defined below, just calls substitute(). Why can’t we use it to define g()? In other words, what will the following code return? First make a prediction. Then run the code and think about the results.

`f <- function(x) substitute(x)
g <- function(x) deparse(f(x))
g(1:10)
g(x)
g(x + y ^ 2 / z + exp(a * sin(b)))`

prediction: the output in each case will be the string "f(x)"
outcome: the output was actually the string "x",
is this due to lazy evaluation?

for the desired output, change the way scoping happens with this:

`h <- function (x) {
  y <- substitute(x)
  deparse(y)
}`



**Nonstandard Evaluation: Nonstandard Evaluation in Subsets**


1. Predict the results of the following lines of code:

eval(quote(  eval(quote(  eval(quote(2 + 2))))))
# 4


eval(  eval(quote(  eval(quote(  eval(quote(2 + 2)))))))
# 4

quote(
  eval(quote(  eval(quote(   eval(quote(2 + 2))))))
  )
# eval(quote(  eval(quote(   eval(quote(2 + 2)))))), a language object


2. subset2() has a bug if you use it with a single column data frame. What should the following code return? How can you modify subset2() so it returns the correct type of object?

sample_df2 <- data.frame(x = 1:10)
subset2(sample_df2, x > 8)
#> [1]  9 10

need output to be a data frame with same names() as input.

`subset3 <- function(x, condition) {
  condition_call <- substitute(condition)
  r <- eval(condition_call, x)
  result <- as.data.frame(x[r,])
  names(result) <- names(x)
  result  
}`


3. The real subset function (subset.data.frame()) removes missing values in the condition. Modify subset2() to do the same: drop the offending rows.



# use !is.na to turn NA into FALSE

`subset4 <- function(x, condition) {
  condition_call <- substitute(condition)
  r <- eval(condition_call, x)
  r <- r & !is.na(r)
  result <- as.data.frame(x[r,])
  names(result) <- names(x)
  result  
}`


4. What happens if you use quote() instead of substitute() inside of subset2()?


`sample_df <- data.frame(a = 1:5, b = 5:1, c = c(5, 3, 1, 4, 1))`

Both versions of subset below throw errors. Look into this later.


`subset5 <- function(x, condition) {
  condition_call <- quote(condition)
  r <- eval(condition_call, x)
  x[r, ]
}`

`subset6 <- function(x, condition) {
  condition_call <- quote(condition)
  r <- eval(condition_call, x, parent.frame())
  x[r, ]
}`



5. The second argument in subset() allows you to select variables. It treats variable names as if they were positions. This allows you to do things like subset(mtcars, , -cyl) to drop the cylinder variable, or subset(mtcars, , disp:drat) to select all the variables between disp and drat. How does this work? I’ve made this easier to understand by extracting it out into its own function.

`select <- function(df, vars) {
  vars <- substitute(vars)
  var_pos <- setNames(as.list(seq_along(df)), names(df))
  pos <- eval(vars, var_pos)
  df[, pos, drop = FALSE]
}
select(mtcars, -cyl)`

var_pos is being used as the environment for eval - it is literally a list of integers named after the dataframe columns. Look at this more later.



5. What does evalq() do? Use it to reduce the amount of typing for the examples above that use both eval() and quote().


evalq() does the same operation as eval(quote()); the difference being that eval(quote()) passes the argument of quote to the


**Nonstandard Evaluation: Scoping Issues**

1. plyr::arrange() works similarly to subset(), but instead of selecting rows, it reorders them. How does it work? What does substitute(order(...)) do? Create a function that does only that and experiment with it.

2. What does transform() do? Read the documentation. How does it work? Read the source code for transform.data.frame(). What does substitute(list(...)) do?

3. plyr::mutate() is similar to transform() but it applies the transformations sequentially so that transformation can refer to columns that were just created:

df <- data.frame(x = 1:5)
transform(df, x2 = x * x, x3 = x2 * x)
plyr::mutate(df, x2 = x * x, x3 = x2 * x)
How does mutate work? What’s the key difference between mutate() and transform()?

4. What does with() do? How does it work? Read the source code for with.default(). What does within() do? How does it work? Read the source code for within.data.frame(). Why is the code so much more complex than with()?

**Nonstandard Evaluation: Calling from another function**

1. The following R functions all use NSE. For each, describe how it uses NSE, and read the documentation to determine its escape hatch.

From documentation: Use the list object to specify objects via a character vector.

so, instead of calling rm(x), call rm(list = x )

* library() and require()

both contain the following conditional statement:
`if (!character.only)
    package <- as.character(substitute(package))`

character.only is an argument that defaults to FALSE, creating the escape hatch for the user.


* substitute()

substitute points to a primitive function. I can't find the built-in escape hatch, and it doesn't seem like it should have one since it is at the heart of non-standard evaluation.




* data()

from documentation: the data sets to be loaded can be specified as a set of character strings or names, or as the character vector 'list', or as both.

so, similar to rm.


* data.frame()

data.frame uses NSE to capture row names, but you can input those yourself using the row.names argument.


2. Base functions match.fun(), page(), and ls() all try to automatically determine whether you want standard or non-standard evaluation. Each uses a different approach. Figure out the essence of each approach then compare and contrast.

match.fun() checks if the input FUN is character, and is either of length 1 or is of type "symbol", and if so does nonstandard evaluation.

page() checks if the input x is character and of length 1, and if so it does standard evaluation, otherwise it uses deparse(substitute())

ls() overwrites itself with substitute, and then checks if name is a character vector, deparsing if it is not.



6. Add an escape hatch to plyr::mutate() by splitting it into two functions. One function should capture the unevaluated inputs. The other should take a data frame and list of expressions and perform the computation.

following Peter's solution

`mutate <- function(df, column_list = NULL, ...){
  # first intermediate function
  dot_column_list <- function(...){
    result <- as.list(substitute(list(...)))
    result <- result [names(result) != ""]
  }
  # second intermediate function
  mutate_l <- function(df, col_list) {
    for (col in names(col_list)){
      df[[col]] <- eval(col_list[[col]], df, parent.frame())
    }
  }
  # begin main function
  if is.null(column_list) {
    column_list <- dot_column_list(...)
  }
  mutate_l(df, column_list)
}
`

7. What’s the escape hatch for ggplot2::aes()? What about plyr::.()? What do they have in common? What are the advantages and disadvantages of their differences?





8. The version of subset2_q() I presented is a simplification of real code. Why is the following version better?

subset2_q <- function(x, cond, env = parent.frame()) {
  r <- eval(cond, x, env)
  x[r, ]
}
Rewrite subset2() and subscramble() to use this improved version.

This version of subset2_q allows for use of a different environment


**Nonstandard Evaluation: Substitute**

Use subs() to convert the LHS to the RHS for each of the following pairs:
a + b + c -> a * b * c
f(g(a, b), c) -> (a + b) * c
f(a < b, c, d) -> if (a < b) c else d
For each of the following pairs of expressions, describe why you can’t use subs() to convert one to the other.
a + b + c -> a + b * c
f(a, b) -> f(a, b, c)
f(a, b, c) -> f(a, b)
How does pryr::named_dots() work? Read the source.



**Nonstandard Evaluation: Downsides**

1. What does the following function do? What’s the escape hatch? Do you think that this is an appropriate use of NSE?

nl <- function(...) {
  dots <- named_dots(...)
  lapply(dots, eval, parent.frame())
}


2. Instead of relying on promises, you can use formulas created with ~ to explicitly capture an expression and its environment. What are the advantages and disadvantages of making quoting explicit? How does it impact referential transparency?
