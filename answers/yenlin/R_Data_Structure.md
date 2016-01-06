Vectors
===========
1. What are the six types of atomic vector? How does a list differ from an atomic vector?

2. What makes is.vector() and is.numeric() fundamentally different to is.list() and is.character()?

3. Test your knowledge of vector coercion rules by predicting the output of the following uses of c():
c(1, FALSE)
c("a", 1)
c(list(1), "a")
c(TRUE, 1L)

4. Why do you need to use unlist() to convert a list to an atomic vector? Why doesn’t as.vector() work?

5. Why is 1 == "1" true? Why is -1 < FALSE true? Why is "one" < 2 false?

6. Why is the default missing value, NA, a logical vector? What’s special about logical vectors? (Hint: think about c(FALSE, NA_character_).)

======================
Attributes and Factors
======================
1. An early draft used this code to illustrate structure():
structure(1:5, comment = "my attribute")
#> [1] 1 2 3 4 5
But when you print that object you don’t see the comment attribute. Why? Is the attribute missing, or is there something else special about it? (Hint: try using help.)

2. What happens to a factor when you modify its levels?
f1 <- factor(letters)
levels(f1) <- rev(levels(f1))

3. What does this code do? How do f2 and f3 differ from f1?
f2 <- rev(factor(letters))

f3 <- factor(letters, levels = rev(letters))

===================
Matrices and arrays
===================
1. What does dim() return when applied to a vector?

2. If is.matrix(x) is TRUE, what will is.array(x) return?

3. How would you describe the following three objects? What makes them different to 1:5?
x1 <- array(1:5, c(1, 1, 5))
x2 <- array(1:5, c(1, 5, 1))
x3 <- array(1:5, c(5, 1, 1))


==============
Data Frame
==============
1. What attributes does a data frame possess?

2. What does as.matrix() do when applied to a data frame with columns of different types?

3. Can you have a data frame with 0 rows? What about 0 columns?

