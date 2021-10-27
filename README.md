# Wine project

*Build a Wine Quality Analytics system to help determine the quality of wines produced based on ingredients & composition.*

For more information, visit [this link](https://archive.ics.uci.edu/ml/datasets/wine+quality).

Input variables (based on physicochemical tests):
1. fixed acidity in g(tartaricacid)/dm3
2. volatile acidity in g(aceticacid)/dm3
3. citric acid in g/dm3
4. residual sugar in g/dm3
5. chlorides in g(sodium chloride)/dm3
6. free sulfur dioxide in mg/dm3
7. total sulfur dioxide in mg/dm3
8. density in g/cm3
9. pH is scaleless
10. sulphates in g(potassiumsulphate)/dm3
11. alcohol in % vol

Output variable (based on sensory data): 
12. quality (score between 0 and 10)


Completed initial data import and check. Confirmed consistent column headers across both datasets and no NaNs.
Correct number of samples as per .names file. 

Removed quotation marks from column headers. Multiple methods were tried, however, only list comprehension method was successful.

Wines grouped into 3 categories: low, medium and high quality.
Wines with a quality score of 3, 4, and 5 are low quality, score of 6 and 7 are medium quality, and score of 8 and 9 are high quality wines.

A third dataset was created, combining both red and white wines. It might be useful for more complex analysis and plots, and will be used to create a Machine Learning algorithm able to predict wine type based on its composition. One of the predictive models can be built to predict the type of wine by looking at the other 12 attributes.

The records were re-shuffled to randomize data points. This was done as there may otherwise be an issue when fitting machine learning model, if for example the dataset is not split in a fair way.

Next, the individual attributes of red and white wines were compared side by side using concat() and describe(). This overview allows for preliminary observations of patterns and a good indication of which attributes to expore in more detail.