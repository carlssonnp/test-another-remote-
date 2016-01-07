**Functions: Primitive Functions**

1. What function allows you to tell if an object is a function? What function allows you to tell if a function is a primitive function?

`is.function` and `is.primitive`

2. Use the code provided to answer the following questions:

* Which base function has the most arguments?

* How many base functions have no arguments? What’s special about those functions?

(I don't know how to extract the number of arguments of a function.)

* How could you adapt the code to find all primitive functions?

replace `is.function` with `is.primitive`

3. What are the three important components of a function?

formals, body, and environment

4. When does printing a function not show what environment it was created in?

when the environment is the global environment



**Functions: Lexical Scoping**

1. the code returns a named vector, with one element `“c” = 10`. `c` is used as a variable name, a name in the vector, and the “combine” operator

2. name masking, recognizing function calls, the "fresh start" principle (every time a function is called, a new environment is created to host execution), and dynamic lookup (lookup happens when the function runs, not when the function is created).

3. 202, the value of `x` doesn't get applied until the innermost function, where `x` is squared.



**Functions: Arguments**

1.
`x <- sample(x = c(1:10, NA), size = 20, replace = TRUE)`
`y <- runif(20)`
`cor(x, y, use = "pairwise.complete.obs", method = "kendall")`

2. returns 3. by name masking (not sure about this?), the default value of `x` assigns a value to `y`, which takes precedence over the default value of `y`.

3. returns 100. by dynamic lookup, `x` is assigned a value of `z`, and `z` is known in the function environment to be `100`.


**Functions: Return Values**

1. (come back to this later)

2. you can undo `library()` with `detach()`

3. function(device,code) {on.exit(dev.off())
  device(code)
}
% not sure about this.
