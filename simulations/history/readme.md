## History of Pulling Credit Data

Back in our day we had to walk 15 miles to get access to credit data and build a model. 

Originally, modeling data was retrieved by going into production console and pulling data by hand, using `RubyRMPI.store` to store data in the Ruby console and then `rubyread` from the R console to read the data.

Then, the Avant package was built on 8 April 2014.  The very [first function added was `batch_data`](https://github.com/avantcredit/avant/commit/66f99662b3257556e21238fa46eb67be71f2064a), designed to provide an API to put an end to this madness and be able to fetch all the model-related data for a given loan and model.  It was ten whole months later [until `batch_source` was added](https://github.com/avantcredit/avant/commit/32ee120a2df467a1136f956418db79f17a674c46) to fetch data on the data source specific level for a given model.


## History of Syberia

#### Avant Credit Model

* The very beginning of modeling at Avant: https://github.com/avantcredit/avant-credit-model
* Started by Jeff O'Dell and John Lynch on 23 May 2013.
* Rob K starts refactoring it on 24 May 2013.  He didn't know any R at this time.  (This means Rob went from 0 to writing stagerunner in 8 months and 23 days.)
* Started out as [classic hack scripts](https://github.com/avantcredit/avant-credit-model/blob/e20457b1fe4fbee1f2b81860456e814f8c35d4c0/Model%20Building.r).
* Everything was done in RStudio and the lack of developer sanity was downright comical (Hack scripts, CSVs commited to the repo, no understanding of how R packages work, private keys commited to the repo, etc.)


#### Primordial Syberia

* Over time, from May to December, avant-credit-model gradually morphed into a proto-Syberia.
* Became [a suite of S4 classes and methods](https://github.com/avantcredit/avant-credit-model/commit/8450db3bd800b131ecdc83d041f321799d428e1c#commitcomment-14215913) and `run` was invented for running models.


#### TODO: Work with Rob to finish the rest.



## History of GBM

 * [Yoav Freund](https://en.wikipedia.org/wiki/Yoav_Freund) & [Robert Schapire](https://en.wikipedia.org/wiki/Robert_Schapire) are credited with the adaBoost algorithim that serves as the foundation of GBM.
 * [Jerome Friedmand](https://statweb.stanford.edu/~jhf/) is largely credited as the driving force behind full-fledged GBM algorithim.
   * 10 minute [video](https://www.youtube.com/watch?v=79tR7BvYE6w) where he is interviewd by [Tibshirani](http://statweb.stanford.edu/~tibs/) & [Hastie](http://web.stanford.edu/~hastie/) on genesis of tree based methods. 
   

## Exercises

1.) Take a brief moment to contemplate and be grateful. Easier said than done. Ok good. Now you can go back to cursing about bugs.       

2.) Go into production console and grab TU313 data for a loan by hand, store it in RubyRMPI and read it back in R.  Then use `batch_source` to get TU313 data for that same loan.  Do the two dataframes match?

3.) Optional Trivia: What Language was original GLMNET package programmed in?
