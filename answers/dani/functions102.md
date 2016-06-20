1. What does the following code return? Why? What does each of the three c’s mean?

c <- 10
c(c = c)

* **first c is a variable set to 10, second c is concat function, third c creates a var equal to value of c (10), and last c calls first c. Returns vector with element c set to 10.**

2. What are the four principles that govern how R looks for values?
* **name masking, functions vs. variables, a fresh start, dynamic lookup**

3. What does the following function return? Make a prediction before running the code yourself.

f <- function(x) {
  f <- function(x) {
    f <- function(x) {
      x ^ 2
    }
    f(x) + 1
  }
  f(x) * 2
}
f(10)

* **returns 202**

Quiz
1. What are the three components of a function?
* **body, formals, environment**

2.What does the following code return?

x <- 10
f1 <- function(x) {
  function() {
    x + 10
  }
}
f1(1)()

* **11**

3. How would you more typically write this code?

`+`(1, `*`(2, 3))

* **2*3+1**

4. How could you make this call easier to read?

mean(, TRUE, x = c(1:10, NA))

* **mean(c(1:10, NA), na.rm = TRUE)**

5. Does the following function throw an error when called? Why/why not?

f2 <- function(a, b) {
  a * 10
}
f2(10, stop("This is an error!"))

* **No, it returns 100. Parameter b is never used in the function**

6.What is an infix function? How do you write it? What’s a replacement function? How do you write it?
* ** infix functions are those whose name comes in between arguments and must be created starting and ending with %.**
* **replacement functions act like they modify arguments in place (in reality a copy in memory is created). They are written like `funcname<-`**




7. What function do you use to ensure that a cleanup action occurs regardless of how a function terminates?

