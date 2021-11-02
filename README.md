# Wine project

*Build a Wine Quality Analytics system to help determine the quality of wines produced based on ingredients & composition.*

For more information, visit [this link](https://archive.ics.uci.edu/ml/datasets/wine+quality).

**Input variables (based on physicochemical tests):**
1. fixed acidity in g(tartaric acid)/L 
2. volatile acidity in g(acetic acid)/L 
3. citric acid in g/L
4. residual sugar in g/L
5. chlorides in g(sodium chloride)/L
6. free sulfur dioxide in mg/L
7. total sulfur dioxide in mg/L
8. density in g/mL
9. pH is scaleless
10. sulfates in g(potassium sulphate)/L
11. alcohol in % vol

Output variable (based on sensory data): 

12. quality (score between 0 and 10)


**Pertinent information**
1. Fixed acidity contributes greatly to the wine’s taste
2. Volatile acidity: process of wine turning into vinegar; a subset of fixed acidity. Legal limits of Volatile Acidity are 1.2 g/L for red wine and 1.1 g/L for white wine (USA)
3. Citric acid is a subset of fixed acidity
4. Residual sugar is sugar remaining after fermentation stops, or is stopped
5. Chlorides can be a significant contributor to saltiness in wine
6. Free sulfur dioxide: the active part of the sulfur dioxide added to wine is said to be free. The winemaker will always try to get the highest proportion of free sulfur to bind
7. Total sulfur dioxide: the sum of the bound and the free SO2. Red wines can only have 160mg/L, while white and rose wines can have about 210mg/L. They are a natural by-product of the fermentation process that work as a preservative against certain yeast and bacteria, which will quickly destroy a wine if they start to multiply. But more are added to help preserve for longer than a few weeks/months.
8. Density: generally used as a measure of the conversion of sugar to alcohol. Link to specific gravity, sugar, potential alcohol.
9. pH: Most wines have a pH between 2.9 and 3.9 
10. Sulfates (potassium metabisulfite) acts as an antioxidant, removing all the oxygen suspended in the wine, which slows down aging. Natural cork closures enable micro-oxygenation by allowing tiny amounts of oxygen back into the wine so flavours can reach their potential.
11. Alcohol 



Completed initial data import and check. Confirmed consistent column headers across both datasets and no NaNs.
Correct number of samples as per .names file. 

Removed quotation marks from column headers. Multiple methods were tried, however, str.strip was used as it only requires one argument.

It was noted that there are roughly 3 times more white wine samples than red wine. This will need to be addressed

Wines grouped into 3 categories: low, medium and high quality.
Wines with a quality score of 3, 4, and 5 are low quality, score of 6 and 7 are medium quality, and score of 8 and 9 are high quality wines.

A third dataset was created, combining both red and white wines. It might be useful for more complex analysis and plots, and will be used to create a Machine Learning algorithm able to predict wine type based on its composition. One of the predictive models can be built to predict the type of wine by looking at the other 12 attributes.

The records were re-shuffled to randomize data points. This was done as there may otherwise be an issue when fitting machine learning model, if for example the dataset is not split in a fair way.

Based on the distribution of quality scores, it was decided to increase the number of labels from three to five. This split out the middle into three categories; medium-low, medium, and medium-high. The aim of this was to extract more meaningful conclusions from data analysed by category. 

Next, the individual attributes of red and white wines were compared side by side using concat() and describe(). This overview allows for preliminary observations of patterns and a good indication of which attributes to expore in more detail.

Distribution of quality is based on human perception and as such caution should be used when correlating specific chemical components. There may not be any extremely strong or consistent correlation to any single attribute. The possible over representation of medium-quality wines also reinforces this idea.

As such, although there are fewer samples of very low and very high quality wine (as judged by the sommeliers), these results actually have higher statistical value as they have the potential to represent clearly definable characteristics of wine, whether positive or negative. Hypothesis testing will therefore focus mostly on these results and what they reveal. However, the newly split middle categories will also be used to determine if there is a trend towards high or low quality with respect to chemical composition.

There was a positive correlation observed between alcohol concentration and quality. It is possible that this is due to the alcohol's ability to deliver dissolved volatiles to the nose. It is recommended to further investigate the alcohol content's correlation with other attributes of the wine to determine if there is a link to quality. 