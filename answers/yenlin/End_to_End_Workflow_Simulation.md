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

