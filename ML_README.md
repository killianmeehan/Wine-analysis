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