
**Advanced R, Data Structures: Vectors**

**Exercises**

1. The six types of atomic vector are logical, integer, double, character, raw, and complex. A list is heterogeneous (i.e. elements in a list can be of different types), a vector is not.

2. is.list() and is.character() return true if the object is a list or a character, respectively, with no additional conditions. is.vector checks for extra attributes, and is.numeric checks if the object can be “reasonably used as a number” (from R documentation of is.numeric) (I’m not totally sure about this!)

3.
`c(1, FALSE)` becomes `1,0`
`c(“a”,1)` becomes `”a”,”1”`
`c(list(1), “a”)` becomes `list(list(1), list(“1”))`
c(TRUE, 1L) becomes `1L, 1L`

4. as.vector() attempts to coerce to a vector, and a list is a more general class of object than a vector, so no coercion happens.

5.
`1 == “1”` coerces the left hand side to `”1”`.
`-1 < FALSE` coerces the right hand side to `0`.
`”one” < 2` coerces the right hand side to `2`.

6. You want `NA` to be at the top of the coercion hierarchy so that it can get “coerced down” to match any type that it is expected to operate with.



**Advanced R, Data Structures: Attributes**

**Exercises**

1. `comment()` is a special attribute, and it has restrictions on the values it can take. (see documentation for attributes)

2. changing the levels does not change the underlying integer sequence, only the sequence at level of “levels”. in this example, `f1` is still the same underlying integer sequence, but the output of `f1` is now the reversed alphabet.

3. the code for `f2` first computes the levels “letters”, and then reverses the underlying integer sequence. so the levels are in alphabetical order and the integer sequence counts down.

the code for `f3` computes is levels from the reversed alphabet. so the levels are in reverse alpha order, and the integer sequence counts down.



**Advanced R, Data Structures: Matrices and Arrays**

**Exercises**

1. `dim()` returns `NULL` for a vector, unless you assign it a value

2. a matrix is a special kind of array, so it returns `TRUE`.

3. these are three-dimensional arrays. the `dim` attribute is different than for a vector.



**Advanced R, Data Structures: Data Frames**

**Exercises**

1. `names()` which are `colnames()`, `rownames()`, `length()` which is `ncol()`, and `nrow()`.

2. it applies coercion rules to obtain an atomic

3. if you reduce the number of rows/columns to  0, the data frame becomes an empty named list.
