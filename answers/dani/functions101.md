14.1.1
1. Why is TRUE not a parameter to rescale01()? What would happen if x contained a single missing value, and na.rm was FALSE?
* **It's not a param because we want to always remove na values otherwise range will return NA NA**

2. Practice turning the following code snippets into functions. Think about what each function does. What would you call it? How many arguments does it need? Can you rewrite it to be more expressive or less duplicative?

mean_values <- function(x) {
	mean(is.na(x))
}
proportion <- function(x) {
	x / sum(x, na.rm = TRUE)
}

variation_coeff <- function(x) {
	sd(x, na.rm = TRUE) / mean(x, na.rm = TRUE)
}

3. Write your own functions to compute the variance and skew of a vector.

variance <- function(x) {
	n <- length(x)
	m <- mean(x)
	((1/(n - 1)) * sum((x - m)^2))
}

skew <- function(x) {
	n <- length(x)
    v <- var(x)
    m <- mean(x)
    sk <- (1/(n - 2)) * sum((x - m)^3)
    sk/(var(x)^(3/2))

}

4. Implement a fizzbuzz function. It take a single number as input. If the number is divisible by three, return “fizz”. If it’s divisible by five return “buzz”. If it’s divisible by three and five, return “fizzbuzz”. Otherwise, return the number.

fizzbuzz <- function(i) {
	 if (i %% 3 == 0 && i %% 5 == 0) {return("FizzBuzz")}
	 else if (i %% 3 == 0) {return("Fizz")}
	 else if (i %% 5 == 0) {return("Buzz")}
	else i
}

5.Write both_na(), a function that takes two vectors of the same length and returns the number of positions that have an NA in both vectors.

both_na <- function(v1, v2) {
	which(s.na(v1) & is.na(v2))
}

6. What do the following functions do? Why are they useful even though they are so short?
is_directory <- function(x) file.info(x)$isdir
is_readable <- function(x) file.access(x, 4) == 0

** is_directory returns True if x is a directory and is_readable returns True if x has read permission.**

14.2.1

1. Read the source code for each of the following three functions, puzzle out what they do, and then brainstorm good names.

f1 <- function(string, prefix) {
  substr(string, 1, nchar(prefix)) == prefix
}
f2 <- function(x) {
  if (length(x) <= 1) return(NULL)
  x[-length(x)]
}
f3 <- function(x, y) {
  rep(y, length.out = length(x))
}

* **f1 could be called is_prefix()**
* **f2 could be called except_last() or get_all_but_last()**
* **f3 could be called rep_y_x_times() or replicate_y()

3. Compare and contrast rnorm() and MASS::mvrnorm(). How could you make them more consistent?
* **both deal with the normal distribution but mvrnorm with the multivatiate normal?**

14.3.4
1. What’s the difference between if and ifelse()? Carefully read the help and construct three examples that illustrate the key differences.
* **if is a flow control construct while ifelse() is an R function that takes in parameters expression, what to do if expression is True and what to do if expression is False. It combines if and else but is not the same as it is intended to work on vectors with length > 1 (returns values for each value of the vector)**

2. Write a greeting function that says “good morning”, “good afternoon”, or “good evening”, depending on the time of day. (Hint: use a time argument that defaults to lubridate::now(). That will make it easier to test your function.)

greeting <- function(time = lubridate::now()) {
	hour <- hour(time)
	if (hour <= 12) {
	print("Goood morning")
} else if (hour < 18) {
	print("Good afternoon")
} else
	print("Good evening")
}

3. How could you use cut() to simplify this set of nested if-else statements?

if (temp <= 0) {
  "freezing"
} else if (temp <= 10) {
  "cold"
} else if (temp <= 20) {
  "cool"
} else if (temp <= 30) {
  "warm"
} else {
  "hot"
}

* **temp %>% cut(c(-Inf,seq(0, 30, 10), inf),  labels = c("freezing", "cold", "cool", "warm", "hot")))**

How would you change the call to cut() if I’d used < instead of <=? What are the advantages of cut() for this type of problem?
* **can not include right = FALSE depending on what end point I want to include**

4. What happens if you use switch() with numeric values?
* **only int values are allowed if value is not a char string and numeric does not allowe default  values**

5. What does this switch() call do?

switch(x, 
  a = ,
  b = "ab",
  c = ,
  d = "cd"
)
* **works like an if / else statement, reassigning values depending on the value of x.**

14.4.5
1. What does commas(letters, collapse = "-") do? Why?
* **gives an error because collapse is not a param to set**

2. It’d be nice if you supply multiple characters to the pad argument, e.g. rule("Title", pad = "-+"). Why doesn’t this currently work? How could you fix it?
* **it works by calling the function as is; pad characters will be pasted**

3. What does the trim argument to mean() do? When might you use it?
* **the fraction of obs to remove from the endpoints of a vector before calculating the mean. We could use it to eliminate outliers**

4. The default value for the method argument to cor() is c("pearson", "kendall", "spearman"). What does that mean? What value is used by default?
* **pearson is the default**


