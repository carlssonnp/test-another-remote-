**Exercise 1:** Watch [Introductory Tutorial on Running a Sbyeria File](https://www.youtube.com/watch?v=mpo8T6TiBvk) (Verify you are signed in through Avant. If one cannot access notify Igor Veksler.)

NOTE: The notation has changed as of time of filming with the addition of data source specific munging.  Therefore to run within specific substage one needs to specifiy additional stage.  To run the first stage of Data Stage, you must `run("demo", to = "data/2/1")` instead of `run("demo", to = "data/1")`.

**Exercise 2:** Read [the documentation on models](https://github.com/avantcredit/avant-analytics/blob/master/models/README.md).

**Exercise 3:** Read [the documentation on monitors](https://github.com/avantcredit/avant-analytics/tree/master/lib/debug/monitors).

**Exercise 4:** Install [Python XGBoost](https://github.com/dmlc/xgboost/tree/master/python-package)

**Exercise 5:** Apply this knowledge to run the following [syberia file](https://github.com/avantcredit/avant-analytics/blob/master/models/examples/demo/demo.R)  

* create a new branch and new directory `demo_<yourname>` 

* Within the export stage change `a` to your name as to create a new model to not overwrite an existing model: `s3 = "model/example/demo/<yourname>"`  

* Submit any errors you experience as an issue within [avant-analytics-scraps](https://github.com/avantcredit/avant-analytics-scraps) and tag Elaine Lee.  It is important you are able to successfully run end to end as the subsequent simulations will use this model as a foundation. 

* Run the demo model completely.

* After "Drop single valued variables" what are the dimensions of the training dataframe? (Hint: use the `dim` monitor.)
