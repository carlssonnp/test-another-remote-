Run a Syberia File
===================
Exercise 2: 
Read the documentation on models. Also read about the avantformula.
Test your knowledge:

1. What is an indicator?
Indicator contains one of the external Github depdendencies and the join key (e.g., customer_id). 

2. How many columns of data are produced by the indicator?
Two columns. One is id and the other is a dependency.

3. Where is the R code for the following found in 'avant' or 'avant-analytics' repos? ** indicators ** mungebits ** models
Indicators: avant-analytics/lib/indicators/
mungebits: avant-analytics/lib/mungebits/
models: avant-analytics/models/

4. What is the source of data when both an s3key and data sources are specified in the import stage?
s3key is the source of data.

5. How does the syberia model file pick up the default parameter values for a model?
This is defined in the model stage. The source can be found at 
avant-analytics/lib/shared/

==============
Exercise 5: 
Apply this knowledge to run the following syberia file. You must use the Beauty or the Beast EC2 instances to finish this exercise. Prior to using the run command, set options(avant.limit = 500) so you don't run on every single loan and waste a lot of time.

Create a new branch and new directory demo_<yourname>

Within the export stage change a to your name as to create a new model to not overwrite an existing model: s3 = "model/example/demo/<yourname>"

Submit any errors you experience as an issue within avant-analytics-scraps and tag Elaine Lee. It is important you are able to successfully run end to end as the subsequent simulations will use this model as a foundation.

Run the demo model completely.

After "Drop single valued variables" what are the dimensions of the training dataframe? (Hint: use the dim monitor.)
