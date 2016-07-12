1. GBM hyperparameters to tune

 tree depth 
 number of leaves 
 n trees
 depth of individual trees
 loss function
 learning rate
 etc

 2. 
 Tree algorithms aren't sensitive to scaling / normaization. Even if we were to scale features, the tree would retain the same structure.

 3. Trees are grown using metrics such as gini and IG, which are measures of impurity. In simple terms, we want to split data on features that give more information than others and reduce imporuty (high mix of classification types). The goal is to get tree leaves that have only one classification. 

 4. 
 In general terms, regularization is the penalty (loss function) we use in models to penalize incorrect classification and model complexity. L1 regularization is least absolute error, it minimuzes the sum of absolute difference between target and estimated value. L2 regularization loss function is the least square error, minimizing the sum of the squared differences. Where it's imposed? During training?

 5.
 There are various stopping criteria to stop growing a tree. These include max depth or when all the samples in leaves have the same classification / you cannot split any farther. As far as how many trees are growth, this is also a criteria that can be specified.
 The great thing about aggregate tree algorithms is that we can allow each tree to individually overfit (no pruning) because in the aggregate this will average out.

 6.
 The gradient is used as we are trying to add new learners which are correlated with the negative gradient of the loss function. Both the gradient and the hessian relate to the derivative of the loss function, which we try to minimize. The hessian is a matrix which has the second partial derivatives of the loss function.

 7. To get the hessian, get the loss function, take the second partial derivatives wrt each variable.

 ####

 