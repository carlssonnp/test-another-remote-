## Reading

Earlier we talked about importing data into Syberia.  But where did this data come from in the first place?

Data starts out in our Ruby application, called [avant-basic](github.com/avantcredit/avant-basic).  It is stored within PostgreSQL databases on Heroku. We retrieve the data in R by calling a Ruby-R API.

* Use `?avant::batch_source` in your R console to read a bit about `batch_source`.  This is the R function used by Syberia to get data.


## Exercises

* Reading through the code of `batch_source` how do you think it gets data (even if you only know vaguely)?
