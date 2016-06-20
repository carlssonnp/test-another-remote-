1. Why are the following two invocations of lapply() equivalent?

trims <- c(0, 0.1, 0.2, 0.5)
x <- rcauchy(100)

lapply(trims, function(trim) mean(x, trim = trim))
lapply(trims, mean, x = x)

* **they are equivalent because in one we are passing trim but in the otehr we use the ... param of lapply**

2. The function below scales a vector so it falls in the range [0, 1]. How would you apply it to every column of a data frame? How would you apply it to every numeric column in a data frame?

scale01 <- function(x) {
  rng <- range(x, na.rm = TRUE)
  (x - rng[1]) / (rng[2] - rng[1])
}

* ** sapply(df, scale01)**
* **nums <- sapply(df, is.numeric)
	sapply(df[ , nums], scale01)**

3. Use both for loops and lapply() to fit linear models to the mtcars using the formulas stored in this list:

formulas <- list(
  mpg ~ disp,
  mpg ~ I(1 / disp),
  mpg ~ disp + wt,
  mpg ~ I(1 / disp) + wt
)

* lapply(formulas, lm)
* for (m in formulas) {
	print(lm(m))
}

4. Fit the model mpg ~ disp to each of the bootstrap replicates of mtcars in the list below by using a for loop and lapply().

bootstraps <- lapply(1:10, function(i) {
  rows <- sample(1:nrow(mtcars), rep = TRUE)
  mtcars[rows, ]
})

* lapply(bootstraps, function(x) {lm(mpg ~ disp)})
* for (b in bootstraps) {
print(lm(mpg ~ disp))
}

5. For each model in the previous two exercises, extract R2 using the function below.
rsq <- function(mod) summary(mod)$r.squared

* **lapply(lapply(formulas, lm), rsq)**
* **lapply(lapply(bootstraps, function(x) {lm(mpg ~ disp)}), rsq)**



