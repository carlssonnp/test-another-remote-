Watch This [Introductory Tutorial on Running a Sbyeria File](https://www.youtube.com/watch?v=mpo8T6TiBvk)(Verify you are signed in through Avant. If one cannot access notify Igor Veksler.)
  * NOTE: The notation has changed as of time of filming with the addition of DSSM(DataSource Specific Munging). 
          Therefore to run within specific substage one needs to specifiy additional stage. I.E.
          Run within First Munge Procedure of Data Stage => ```r run('demo', to = 'data/2/1/')```

Apply this knwoledge to run the following [syberia file](https://github.com/avantcredit/avant-analytics/blob/master/models/examples/demo/demo.R)  
  * Locally Within the Export stage change `a` to your name as to create a new model to not overwrite an existing model. I.e. `s3 =  "model/example/demo/<yourname>",`  
  * Verify Python [XGBoost Installed](https://github.com/dmlc/xgboost/tree/master/python-package)
  * Submit any errors you experience as an issue within [avant-analytics-scraps](https://github.com/avantcredit/avant-analytics-scraps) and tag Elaine Lee
  * It is important you are able to successfully run end to end as the subsequent simulations will use this model as a foundation. 

Question(s):  
  1) After "Drop single valued variables" what is the size of the training dataframe?
  2) What is the object size of the saved TundraContainer (Hint: Use the s3 commandLine Interface)(Hint2: use `-H` for human readable formatting)






