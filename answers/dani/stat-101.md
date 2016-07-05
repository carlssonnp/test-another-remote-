problems 1, 2, 5, and 6 from Chapter 2 of Introduction to Statistical Learning

1. 
a. A flexible (non parametric) model could perform better since we have many obserations and few parameters. Having many observations allows us to better predict using non parametric models.

b. An inflexible model (parametric) would best suit this situation because a non parametric model needs many obserations to be accurate. 

c. As a highly non-linear relationship, a flexible model would be best as we'd not be restricted by model assumptions. We would still have to be careful of overfitting.

d. High error variance is not a great situation for either flexible or inflexible models as we cannot reduce population error.

2.
a. This is a regression inference problem, as we're interested in the factors that affect salary, not classifying salary in any way or predicting it.  N = 500, p = 4

b. Classification , prediction task. N = 20, P = 13

c. Regression prediction task. N = 52, P = 4.

5. 
Choosing a flexible or inflexible model depends on our goal. A less flexible model could be more important if interpretability (such as explaining the model to clients or investors) is key. A high flexibility model is less interpretable, but could perform better if our task is predictive and we have many obserations. Typically, but not always, classification is predictive so we'd consider a flexible model, while regression is an inferential task, so we could stick to non-flexible models, such as linear regression, despite their assumption overhead.

6. 
A parametric model makes assumptions about the functional form and distribution of the data generating function, while a non-parametric model makes little to no assumptions. A non-parametric model has advantages such as better prediction of train data (but could be a problem to overfitting), but may be hard to interpret. A parametric model limits us to the model assumption, but could be a good approach to retain interpretability. Finally, if we have a small sample size, a non-parametric model may not be of good use. 


CV

It's important to have a validation set AND a test set because we want to evaluate our model on data that the model has never seen! k fold CV is a technique to train and test data on separate folds - keeping 4/5 of data for training and test on the remaining 1/5, and then picking another 4/5 and testing on another 1/5, etc. The validation set is used to select the best model, but we use the test set as an out of sample dataset to measure the error. A disadvantage of doing a 60/20/20 k fold CV is that model selection is done on only 20% of the data.

