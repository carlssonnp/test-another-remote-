## Reading

Earlier we talked about importing data into Syberia.  But where did this data come from in the first place?

Data starts out in our Ruby application, called [avant-basic](github.com/avantcredit/avant-basic).  It is stored within PostgreSQL databases on Heroku. We retrieve the data in R by calling a Ruby-R API.

* Use `?avant::batch_source` in your R console to read a bit about `batch_source`.  This is the R function used by Syberia to get data.

* Skim [some slides about how data goes from the Ruby app into our R consoles](https://docs.google.com/presentation/d/1xii3buvX1QCSPH8TBdemaT3xnxvikjGEYdITiXwA9js).  It's not pretty and it is likely going to change a lot in early 2015.


## Exercises

* Try calling batch_source to get transunion313 data for a random customer.  What is the size of the dataframe you get back?
* What is the role of `request_operation` in getting data?
* Which file does `avant-basic` use to process requests for data?
