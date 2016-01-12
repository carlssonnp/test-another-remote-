Syberia model files are the essential elements for training predictive models for Avant.  Understanding how these predictive models are built starts with a through understanding of syberia model files and how to use them.

**Exercise 1:** (*Important*) Watch [Introductory Tutorial on Running a Syberia File](https://www.youtube.com/watch?v=mpo8T6TiBvk) (Verify you are signed in through Avant. If one cannot access notify Igor Veksler.)

NOTE: The notation has changed as of time of filming with the addition of data source specific munging.  Therefore to run within specific substage one needs to specifiy additional stage.  To run the first stage of Data Stage, you must `run("demo", to = "data/2/1")` instead of `run("demo", to = "data/1")`.

**Exercise 2:**  Read [the documentation on models](https://github.com/avantcredit/avant-analytics/blob/master/models/README.md). Also [read about the avantformula](https://github.com/avantcredit/avantformula/blob/master/README.md).

Test your knowledge:
* What is an indicator?
* How many columns of data are produced by the indicator?
* Where is the R code for the following found in 'avant' or 'avant-analytics' repos?
** indicators
** mungebits
** models
* What is the source of data when both an s3key and data sources are specified in the import stage?
* How does the syberia model file pick up the default parameter values for a model?


**Exercise 3:** Read [the documentation on monitors](https://github.com/avantcredit/avant-analytics/tree/master/lib/debug/monitors).

**Exercise 4:**  Install [Python XGBoost](https://github.com/dmlc/xgboost/tree/master/python-package)
NOTE: This does not work without additional requirements.  Besides, this is only necessary when one wishes to **train** xgb models.  It is not necessary for **predictions**.   Instead, one needs to learn how to use the `beauty` or the `beast` to train their models, where xgb is preinstalled and preconfigured.

**Exercise 5:**  Apply this knowledge to run the following [syberia file](https://github.com/avantcredit/avant-analytics/blob/master/models/examples/demo/demo.R). You must use the Beauty or the Beast EC2 instances to finish this exercise.  Prior to using the `run` command, set `options(avant.limit = 500)` so you don't run on every single loan and waste a lot of time.

* Create a new branch and new directory `demo_<yourname>` 

* Within the export stage change `a` to your name as to create a new model to not overwrite an existing model: `s3 = "model/example/demo/<yourname>"`  

* Submit any errors you experience as an issue within [avant-analytics-scraps](https://github.com/avantcredit/avant-analytics-scraps) and tag Elaine Lee.  It is important you are able to successfully run end to end as the subsequent simulations will use this model as a foundation. 

* Run the demo model completely.

* After "Drop single valued variables" what are the dimensions of the training dataframe? (Hint: use the `dim` monitor.)
