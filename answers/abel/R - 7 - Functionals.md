**Functionals: looping patterns**

1. Why are the following two invocations of lapply() equivalent?

`trims <- c(0, 0.1, 0.2, 0.5)
x <- rcauchy(100)

lapply(trims, function(trim) mean(x, trim = trim))
lapply(trims, mean, x = x)`

In the second invocation, the function mean is being called, the first argument is assigned by `x = x`, so `lapply` figures out to use trims to provide the second argument.


2. The function below scales a vector so it falls in the range [0, 1]. How would you apply it to every column of a data frame? How would you apply it to every numeric column in a data frame?

`scale01 <- function(x) {
  rng <- range(x, na.rm = TRUE)
  (x - rng[1]) / (rng[2] - rng[1])
}`


# applying scale01 to each column of mtcars
`lapply(mtcars, scale01)`

#creating a wrapper around scale01 to only alter numeric rows
`scale02 <- function(x) {
  if (is.numeric(x)) {scale01(x)}
  else {x}
}`

#applying scale02 to each column of mtcars
`lapply(mtcars, scale02)`



3. Use both for loops and lapply() to fit linear models to the mtcars using the formulas stored in this list:

`formulas <- list(
  mpg ~ disp,
  mpg ~ I(1 / disp),
  mpg ~ disp + wt,
  mpg ~ I(1 / disp) + wt
)`

# solution using lapply
`lapply(formulas, function(item) lm(item, mtcars))`

# solution using for loop
`out_exercise_3 <- vector("list", length(formulas))
for (i in seq_along(formulas)) {
  out_exercise_3[[i]] <- lm(formulas[[i]], mtcars)}
out_exercise_3`


4. Fit the model mpg ~ disp to each of the bootstrap replicates of mtcars in the list below by using a for loop and lapply(). Can you do it without an anonymous function?

`bootstraps <- lapply(1:10, function(i) {
  rows <- sample(1:nrow(mtcars), rep = TRUE)
  mtcars[rows, ]
})`

#creating function to apply linear model
`linear_mpg_vs_display <- function(df) {
 lm(mpg ~ disp, df)
}`

#applying the model to bootstraps
`out_exercise_4 <- lapply(bootstraps, linear_mpg_vs_display)`



5. For each model in the previous two exercises, extract R2 using the function below.


`rsq <- function(mod) summary(mod)$r.squared
lapply(out_exercise_3, rsq)`


**Functionals: for loop functionals**

1. Use vapply() to:

* Compute the standard deviation of every column in a numeric data frame.

`function(df) {
 vapply(df, sd, 0)
}`

* Compute the standard deviation of every numeric column in a mixed data frame. (Hint: you’ll need to use vapply() twice.)

`sd_numeric_check <- function(x) {
  if (is.numeric(x)) {scale01(x)}
  else {"not numeric"}
}``







2. Why is using sapply() to get the class() of each element in a data frame dangerous?

(look into this later.)

3. The following code simulates the performance of a t-test for non-normal data. Use sapply() and an anonymous function to extract the p-value from every trial.

`trials <- replicate(
  100,
  t.test(rpois(10, 10), rpois(7, 10)),
  simplify = FALSE
)`
Extra challenge: get rid of the anonymous function by using [[ directly.

4. What does replicate() do? What sort of for loop does it eliminate? Why do its arguments differ from lapply() and friends?

`replicate` creates multiple copies of an object and binds them together into one larger object. The code below illustrates what `replicate` does:

`replicate <- function(n, input) {
 output <- null
 for (i in 1:n) {
  c(output, input)
 }
 output
}`

The argument choice for `replicate()` emphasizes the number of repetitions, so the length of the output should be seen as "variable"; contrast with `lapply` where the length of the output agrees with the length of the list inputl

5. Implement a version of lapply() that supplies FUN with both the name and the value of each component.

`lapply2 <- function(FUN, input_list){
 output <- vector("list", length(formulas))
 for (i in seq_along(input_list)) {
  output[[i]] <- FUN(input_list[[i]], names(input_list[i]))
 }
 output
}`

6. Implement a combination of Map() and vapply() to create an lapply() variant that iterates in parallel over all of its inputs and stores its outputs in a vector (or a matrix). What arguments should the function take?



7. Implement mcsapply(), a multicore version of sapply(). Can you implement mcvapply(), a parallel version of vapply()? Why or why not?

(not sure what the question is asking for.)




**Manipulating Matrices and Data Frames**

1. How does apply() arrange the output? Read the documentation and perform some experiments.

2. There’s no equivalent to split() + vapply(). Should there be? When would it be useful? Implement one yourself.

3. Implement a pure R version of split(). (Hint: use unique() and subsetting.) Can you do it without a for loop?

4. What other types of input and output are missing? Brainstorm before you look up some answers in the plyr paper.
