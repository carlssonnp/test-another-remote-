

**Advanced R, Functions: Lexical Scoping**

**Exercises**

1. the code returns a named vector, with one element `“c” = 10`. `c` is used as a variable name, a name in the vector, and the “combine” operator

2. name masking, recognizing function calls, the "fresh start" principle (every time a function is called, a new environment is created to host execution), and dynamic lookup (lookup happens when the function runs, not when the function is created).

3. 202, the value of `x` doesn't get applied until the innermost function, where `x` is squared.

**Advanced R, Functions: Arguments**

**Exercises**

1.
`x <- sample(x = c(1:10, NA), size = 20, replace = TRUE)`
`y <- runif(20)`
`cor(x, y, use = "pairwise.complete.obs", method = "kendall")`

2. returns 3. by name masking (?), the default value of `x` assigns a value to `y`, which overwrites the default value of `y`.

3. returns 100. by dynamic lookup, `x` is assigned a value of `z`, and `z` is known in the function environment to be `100`.


**Advanced R, Functions: Return Values**

**Exercises**

1. (come back to this later)

2. you can undo `library()` with `detach()`

3. function(device,code) {on.exit(dev.off())
  device(code)
}
% not sure about this.
