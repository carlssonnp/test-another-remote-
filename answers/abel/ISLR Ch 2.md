**ISL, Chapter 2 Exercises**

1. For each of parts (a) through (d), indicate whether we would generally expect the performance of a flexible statistical learning method to be better or worse than an inflexible method. Justify your answer.

a) The sample size n is extremely large, and the number of predictors p is small.

flexible: Having a large sample size makes it harder for overfitting to occur, and the flexible model will gain more from a larger sample size.


b) The number of predictors p is extremely large, and the number of observations n is small.

inflexible: the more flexible method needs a larger sample size to reduce variance and avoid overfitting.


c) The relationship between the predictors and response is highly non-linear.

flexible: If the relationship is highly non-linear, then it is probably better to use a flexible method - an inflexible linear method would always be far from the truth.

d) The variance of the error terms, i.e. σ2 = Var(ε), is extremely high.

inflexible: With a high variance, there will be a lot of noise, and a flexible method will very likely try to model that noise, leading to overfitting.


2. Explain whether each scenario is a classification or regression problem, and indicate whether we are most interested in inference or prediction. Finally, provide n and p.
a) We collect a set of data on the top 500 firms in the US. For each firm we record profit, number of employees, industry and the CEO salary. We are interested in understanding which factors affect CEO salary.


inference: we want to understand how factors affect salary, so we care about the mathematical model.
regression: the response variable is numeric (CEO salary in currency units).

n = 500 (top firms)
p = 3 (record profit, number of employees, and industry)



b) We are considering launching a new product and wish to know whether it will be a success or a failure. We collect data on 20 similar products that were previously launched. For each product we have recorded whether it was a success or failure, price charged for the product, marketing budget, competition price, and ten other variables.


prediction: we want to know whether it will succeed or fail, but do not care about how the input variables affect this.
classification: the response variable is categorical (possible values are "success" and "failure".)

n = 20 (previously launched similar products)
p = 13 (price charged for the product, marketing budget, competition price, and ten other variables)



c) We are interesting in predicting the % change in the US dollar in relation to the weekly changes in the world stock markets. Hence we collect weekly data for all of 2012. For each week we record the % change in the dollar, the % change in the US market, the % change in the British market, and the % change in the German market.


prediction: we want to predict the % change in the US dollar, but we are not asking for precise descriptions of the relationships between the output variable and the input variables.
regression: our response variable is a % change, hence is numeric.

n = 52 (number of weeks in 2012)
p = 3 (% change in the US market, the % change in the British market, and the % change in the German market)



5. What are the advantages and disadvantages of a very flexible (versus a less flexible) approach for regression or classification? Under what circumstances might a more flexible approach be preferred to a less flexible approach? When might a less flexible approach be preferred?


From p. 25: "In general, as the flexibility of a method increases, its interpretability decreases."

A flexible approach may be a better choice when predicting, since it would lead to complicated estimates of the predicting function, where it would be difficult to understand how an individual input variable affects the response variable. A less flexible approach may be preferred when the goal is inference, since such a model will generally make it easier to see the effect of a given input variable with the response variable.



6. Describe the differences between a parametric and a non-parametric statistical learning approach. What are the advantages of a parametric approach to regression or classification (as opposed to a non-parametric approach)? What are its disadvantages?

p. 22-23

In parametric statistical learning, a functional form for the predicting function is chosen in advance, and the machine optimizes parameters (e.g. by choosing a linear model, we need only calculate coefficients). In non-parametric statistical learning, the functional form of the predicting function is chosen by the machine.

In the parametric approach, you run the risk of choosing a form for the prediction function that is far from the truth, and the model will never be able to predict properly (imagine using a linear model to predict exponential growth). In the non-parametric approach, since you need to determine the for of the prediction function "from scratch", you need a very large number of observations to get a useful prediction function.
