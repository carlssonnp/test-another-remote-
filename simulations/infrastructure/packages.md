## Our R Package Ecosystem

So we know the core R packages that make up Syberia (syberia + tundra + director + stagerunner + mungebits2).  And you learned about devtools, magrittr, plyr, and dplyr from reading "Advanced R", "R Packages", and "R For Data Science" by Hadley Wickham.

But what other R packages do we use?

* [S3MPI](https://github.com/robertzk/s3mpi) - Read R objects from S3 and store objects in S3 for others to read.

* [Batchman](https://github.com/peterhurford/batchman) - Run R code in arbitrary batches.

* [Microserver](https://github.com/robertzk/microserver) - a simple web server for R.  We use this to deploy R models as APIs that can return scores.

* [Lockbox](https://github.com/robertzk/lockbox) - package management for R.

* [Testthatsomemore](https://github.com/robertzk/testthatsomemore) - extends `testthat` to include mocking file structures and mocking the system time.  (Also includes some features that are now part of testthat, such as mocking functions and pending tests.)

* [DBTest](https://github.com/avantcredit/dbtest) - extends `testthat` to test database implementations.

#### Exercises

* How do I use the `s3cmd` command line tool to find the size of an S3 object?  How do I use `pryr::object_size` to see the size of that object in R?  Why might these two numbers be different?

* How do I write a test to check that the "cache" table exists in my database?

* How do I write a test that executes as if it was one day prior to right now?

* What does `stop = TRUE` do in batchman?

* How do I use lockbox to install a package from my local directory?
