Make a function that takes another function and returns a function that will print all the arguments and then run the orginal function.

arg_printer <- function(f) {
	print_run <- function(...) {
		cat(paste0("I was called with ",match.call(), ".\n"))
		f(...)
	}
}


Make a function errors_are_nas that takes an expression and returns an NA if that expression fails instead of an error.

errors_are_nas <- function(e) {
  tryCatch(e, error = function(err) NA
  )
}

Optional Read on R6 classes. Try constructing a bank account class with deposit, check balance, and withdraw methods.

Account <- R6Class("Account",
  public = list(
  	balance = 0,
    initialize = function(balance) {
      self$balance <- balance
      self$greet()
    },
    check_balance = function() {cat(paste0("Your current balance is ", self$balance, ".\n"))
    },
    deposit = function(val) {
      self$balance <- self$balance + val
      self$check_balance()
	},
    withdraw = function(val) {
      self$balance <- self$balance - val
      self$check_balance()
	},
    greet = function() {cat(paste0("Hello, your initial balance is ", self$balance, ".\n"))
    }
  )
)
