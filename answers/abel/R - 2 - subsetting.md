
**Subsetting: Data Frames**

1.
Replace `=` with `==`: `mtcars[mtcars$cyl == 4, ]`
Replace `-1` with `1`: `mtcars[1:4, ]`
Add `,` after `5`: `mtcars[mtcars$cyl <= 5,]`
Add `mtcars$cyl == ` before `6`: `mtcars[mtcars$cyl == 4 | mtcars$cyl == 6, ]`

2. (from documentation for “`[`”) NA gets special treatment in indexing, and will return NA. NA_real_ gets coerced to an integer which doesn’t match any indices.

3. (from documentation for “upper.tri”) `upper.tri()` returns a matrix of the same size as the given matrix, with

4. `mtcars[1:20]` is trying to pull the first 20 columns of the data frame, and there are only 11. `mtcars[1:20,]` treats the data frame as a two-dimensional array and pulls the first 20 rows (while still remembering the data frame type).



**Subsetting: Operators**

1. `function(model) {model$df.residual}`
