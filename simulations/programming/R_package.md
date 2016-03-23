## Reading

1) Read the following chapters of "R Packages" by Hadley Wickham:

* ["Package Structure"](http://r-pkgs.had.co.nz/package.html)
* ["Package Metadata"](http://r-pkgs.had.co.nz/description.html)
* ["Object Documentation"](http://r-pkgs.had.co.nz/man.html)

## Trivia Exercises

1. What are the three requirements when naming an R package?
2. Why is it a bad idea to name your package with a "."?
3. What is the difference between `devtools::install_github` and `install.packages`?
4. What is the difference between `Suggests` and `Imports`?
5. What is the importance of `dontrun`?
6. Why do packages have versions?
7. What does moving from v1.0.1 to v2.0.0 mean?  What does moving from v1.0.1 to v1.0.2 mean?
8. What does v1.0.1.9000 mean?

## Simulation Exercise

Write a package with a function called `mean_impute` that takes a vector that can contain NAs and returns a vector with the NAs imputed with the mean of that vector.  Make your package available open source on your GitHub so people can use it!
