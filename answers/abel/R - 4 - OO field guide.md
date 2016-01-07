**OO Field Guide: S3**

1. Read the source code for `t()` and `t.test()` and confirm that `t.test()` is an S3 generic and not an S3 method. What happens if you create an object with class `test` and call `t()` with it?

If you create an object with class `test` and call `t()` with it, R will run `t.test()` (the statistical test, instead of the matrix operation).

E.g. `{x <- "a", class(x) <- "test", t(x)}` tries to run the statistical test, while `{y <- "a", t(y)}` tries to run the matrix operation.


2. What classes have a method for the Math group generic in base R? Read the source code. How do the methods work?

I am confused by this. For instance, `abs()` is a function Math group generic, and takes as an input a numeric vector...

I don't know how to ask R for all classes for which `abs()` has a method.

3. R has two classes for representing date time data, `POSIXct` and `POSIXlt`, which both inherit from `POSIXt`. Which generics have different behaviours for the two classes? Which generics share the same
behaviour?

`> intersect(methods(class = "POSIXct"), methods(class = "POSIXlt"))
[1] "coerce,oldClass,S3-method"   "initialize,oldClass-method"
"show,oldClass-method"
[4] "slotsFromS3,oldClass-method"`


**OO Field Guide: S4**

1. Which S4 generic has the most methods defined for it? Which S4 class has the most methods associated with it?

2. What happens if you define a new S4 class that doesn’t “contain” an existing class? (Hint: read about virtual classes in ?Classes.)

3. What happens if you pass an S4 object to an S3 generic? What happens if you pass an S3 object to an S4 generic? (Hint: read ?setOldClass for the second case.)
