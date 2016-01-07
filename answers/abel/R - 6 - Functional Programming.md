**Functional Programming: Anonymous Functions**

1. Given a function, like "mean", match.fun() lets you find a function. Given a function, can you find its name? Why doesn’t that make sense in R?

No, because functions don't always have names.

2. Use lapply() and an anonymous function to find the coefficient of variation (the standard deviation divided by the mean) for all columns in the mtcars dataset.

`lapply(mtcars, function (x) {sd(x)/mean(x)})`

3. Use integrate() and an anonymous function to find the area under the curve for the following functions. Use Wolfram Alpha to check your answers.

y = x ^ 2 - x, x in [0, 10]
y = sin(x) + cos(x), x in [-π, π]
y = exp(x) / x, x in [10, 20]

`funs <- list( function(x) {x^2 - x}, function(x) {sin(x) + cos(x)}, function(x) {exp(x)/x})
 lowers <- list(0, -pi(), 10)
 uppers <- list(10, pi(), 20)
 result <- mapply(integrate, f = funs, lower = lowers, upper = uppers)
 unlist(lapply(1:3, function(x) {result[[x]]}))`

4. A good rule of thumb is that an anonymous function should fit on one line and shouldn’t need to use {}. Review your code. Where could you have used an anonymous function instead of a named function? Where should you have used a named function instead of an anonymous function?

  I don't know what code the question wants me to look at.


**Functional Programming: Closures**

1. Why are functions created by other functions called closures?

The output functions enclose (i.e. keep a copy of) the environment in which they were created.


2. What does the following statistical function do? What would be a better name for it? (The existing name is a bit of a hint.)

`bc <- function(lambda) {
  if (lambda == 0) {
    function(x) log(x)
  } else {
    function(x) (x ^ lambda - 1) / lambda
  }
}`



3. What does `approxfun()` do? What does it return?

`approxfun()` returns a function that inputs `x`, outputs `y`, and creates a piecewise linear function `y = f(x)` passing through the points in the list given to `approxfun` as two lists.


4. What does `ecdf()` do? What does it return?

`edcf()` returns a step function integer -> integer, inputs in the range min(input) to max(input), outputs in the range 0 to 1.

5. Create a function that creates functions that compute the ith central moment of a numeric vector. You can test it by running the following code:

`m1 <- moment(1)
m2 <- moment(2)

x <- runif(100)
stopifnot(all.equal(m1(x), 0))
stopifnot(all.equal(m2(x), var(x) * 99 / 100))`


`moment <- function(i) {function(x) {xbar <- mean(x)
  mean((x-xbar)^i) }}`



6. Create a function pick() that takes an index, i, as an argument and returns a function with an argument `x` that subsets `x` with `i`.


`pick <- function(x) { function(list_item) { list_item[[x]] } }`




**Functional Programming: Lists of Functions**

Exercises
1. Implement a summary function that works like base::summary(), but uses a list of functions. Modify the function so it returns a closure, making it possible to use it as a function factory.

`custom_summary <- function(list_fcns) { function (x) {
 lapply(list_fcns, function(item) {item(x)})  
 }
}`

2. Which of the following commands is equivalent to `with(x, f(z))`?

`x$f(z)`
