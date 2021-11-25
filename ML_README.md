Machine learning algorithm to determine wine quality
Determining wine type is not considered a useful exercise at this point (based on the requirements of the project)

Based on the very different profiles of red and white wine (seen in the distribtion of sulphides, residual sugar etc from the EDA), it was determined that these two datasets should be trated separately rather than together. The stark difference in dataset size also led to this decision. As such, one model will be run for red, and another for white. 

As the stated goal of this exercise is to predict the wine quality, this would be classified as categorical data (Low/Medium/High quality). This will influence the approach as some ML models do not deal well with categorical data. It is also discrete, as opposed to continuous, because we are dealing with individual bottles of wine rather than e.g. windspeed measurements. (DOUBLE CHECK CORRECT INTERPRETATION)

We want to use supervised learning, as this in essence tells the model what to look for and expect. We know what we are looking for - in this case, a reliable way to determine if a wine is of a certain quality depending on its chemical attributes - therefore it makes sense to use a supervised ML model in this instance. If, however, we were not aware 


LightGBM grows tree vertically while other tree based learning algorithms grow trees horizontally. 
It means that LightGBM grows tree leaf-wise while other algorithms grow level-wise. It will choose 
the leaf with max delta loss to grow. When growing the same leaf, leaf-wise algorithm can reduce more 
loss than a level-wise algorithm.

Important points about tree-growth
If we grow the full tree, best-first (leaf-wise) and depth-first (level-wise) will result in the same tree. The difference is in the order in which the tree is expanded. Since we don't normally grow trees to their full depth, order matters.

Application of early stopping criteria and pruning methods can result in very different trees. Because leaf-wise chooses splits based on their contribution to the global loss and not just the loss along a particular branch, it often (not always) will learn lower-error trees "faster" than level-wise.

For a small number of nodes, leaf-wise will probably out-perform level-wise. As we add more nodes, without stopping or pruning they will converge to the same performance because they will literally build the same tree eventually.

XGBoost is a very fast and accurate ML algorithm. But now it's been challenged by LightGBM — which runs even faster with comparable model accuracy and more hyperparameters for users to tune.

The key difference in speed is because XGBoost split the tree nodes one level at a time and LightGBM does that one node at a time.

So XGBoost developers later improved their algorithms to catch up with LightGBM, allowing users to also run XGBoost in split-by-leaf mode (grow_policy = ‘lossguide’). Now XGBoost is much faster with this improvement, but LightGBM is still about 1.3X — 1.5X the speed of XGB.

LightGBM is susceptible to overfitting on small datasets so be careful!


Cohen’s kappa is more informative than overall accuracy when working with unbalanced data. Keep this in mind when you compare or optimize classification models!
Take a look at the row and column totals in the confusion matrix. Are the distributions of the target/predicted classes similar? If they’re not, the maximum reachable Cohen’s kappa value will be lower.
The same model will give you lower values of Cohen’s kappa for unbalanced than for balanced test data.
Cohen’s kappa says little about the expected accuracy of a single prediction 


Permutation feature importance is a model inspection technique that can be used for any fitted estimator when the data is tabular. This is especially useful for non-linear or opaque estimators. The permutation feature importance is defined to be the decrease in a model score when a single feature value is randomly shuffled 1. This procedure breaks the relationship between the feature and the target, thus the drop in the model score is indicative of how much the model depends on the feature. This technique benefits from being model agnostic and can be calculated many times with different permutations of the feature.

Warning Features that are deemed of low importance for a bad model (low cross-validation score) could be very important for a good model. Therefore it is always important to evaluate the predictive power of a model using a held-out set (or better with cross-validation) prior to computing importances. Permutation importance does not reflect to the intrinsic predictive value of a feature by itself but how important this feature is for a particular model.