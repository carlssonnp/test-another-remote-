**Run a Syberia File - Exercise 2**

* What is an indicator?

The Avant adapter for importing uses the form

indicator ~ source + another_source + etc

the indicator is the part before the `~`;it chooses the dependent variable for the model and pulls the loan ids.

* How many columns of data are produced by the indicator?

Two columns: loan_id and dep_var.

* Where is the R code for the following found in 'avant' or 'avant-analytics' repos? ** indicators ** mungebits ** models

indicators are in avant-analytics/lib/indicators/
mungebits are in avant-analytics/lib/mungebits/
models are in avant-analytics/models/

* What is the source of data when both an s3key and data sources are specified in the import stage?

guessing: The S3 cloud space that Avant buys from Amazon. A non-file source would trigger a call to batch_source, which reads from S3 using the ruby api.


* How does the syberia model file pick up the default parameter values for a model?

From the classifier called in the model stage of the model card.


**Run a Syberia File - Exercise 5**
