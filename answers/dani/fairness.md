1. ML is prone to unfairness because minorities are underrepresented in data. With more data for majority populations and less for "protected classes", algorithms will perform better in prediction and inference on the majority. 

2. We talk about fairness mathematically by discussing the correlation between class membership and outcome. Fairness is calculated with conditional probabilities. We want the probability of a favorble outcome given being a member of a majority class to be equal to the probability of a favorable outcome given membership to a protected class.

3. We can do things like weighted models or other tricks to balance the protected and majority class. In general, we want to keep in mind that our data is biased toward the majority population.

4. Our customers are people, not institutions or businesses, so we have to take care that our algorithms work well at predicting (and not discriminating) when they encounter a member of the protected class or the majority class.

5. If our model doesn't predict well for a protected class - say it says members of a protected class won't pay their loans back - then our models may push us to offer loans to the majority population, while ignoring an important consumer base. 