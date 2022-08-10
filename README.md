# Hospital-Ratings

**Predicting Hospital Ratings**

by Senait Abate



***Business problem:***

The goal of this project is to predict hospital rating and performance compared to the national average performance of hospitals overall in the United States. 


***Data:***

This dataset was acquired from the CORGIS Dataset Project. "The data set allows consumers to directly compare across hospitals performance measure information related to heart attack, emergency department care, preventive care, stroke care, and other conditions. The data is part of an Administration-wide effort to increase the availability and accessibility of information on quality, utilization, and costs for effective, informed decision-making."

Source: https://corgis-edu.github.io/corgis/csv/hospitals/ 

Source: https://data.cms.gov/provider-data/?redirect=true 


***Methods:***

The target was overall rating. Overall rating is an ordinal feature on a scale of 1 to 5, 1 being the lowest and 5 being the higest. For example, a rating of 3 means that the hospital rating is average and falls along the national average rating of most hospitals in the United States. A rating of 2 means that the hospital is below the national average rating. There were at least 4 other features related to various ratings and this was dropped from the dataset to prevent knowing too much about the target variable. Other features included quality of care, value, and costs of procedures due to heart heart attack, heart failure, pneumonia, and hip and knee surgery. After preprocessing, classification models such as KNN and Random Forest Regressor were used and different hyperparameters and metrics were applied to increase the accuracy and performance of these models. A sequential model ws also analyzed to see if overftting could be reduced.


***Results:***

![image](https://user-images.githubusercontent.com/105686944/184013289-6752a7c5-4b35-4cc0-9c9f-b4ffe0b5097f.png)

Heart failure costs are slightly higher than heart attack costs at 4 and 3 rated hospitals. Heart attack costs are higher than heart failure costs at 1 rated hospitals. In general, heart failure and heart attack costs decrease the higher the hospital rating. 


![image](https://user-images.githubusercontent.com/105686944/184013427-d3bec044-8406-42fd-a50a-d2b317375e46.png)

The trend in the above barplot shows the higher the hospital rating the lower the costs for pneumonia procedures while costs for hip and knee procedures fluctuate more with a average rating of 3 having the least cost.


![image](https://user-images.githubusercontent.com/105686944/184040671-12b2f97e-ec04-45ef-af64-8da995ad68d7.png)


Almost half of the hosptial information collected are from private hospitals. The second most type of hospital is an almost equal distribution of government and proprietary hospitals. Church hospitals and those with unknown facility type are the least sampled.   


![newplot (1)](https://user-images.githubusercontent.com/105686944/183523089-9b1a42fa-9d71-4430-a0d9-e7cd58483735.png)

The average cost of care for four procedures were included in the data: heart attack, heart failure, pneumonia, and hip and knee procedures. The US map shows the average cost of hip and knee procedures per state. To get this information, the average costs of care for each hospital for a particular state was added together and the mean was calculated. Certain states, such as Florida and Massachusetts have one some of the highest costs in the country.


***Model:***

Multiple models were analzyed and evaluated in order to find the best predictable model for this regression problem. First, linear regression model was analyzed. The baseline model started off with an R2 value of the training set that can explain 77% variation in the model. However, this does not translate to the test set. For the test set, the R2 value was -1 which is very overfit. This means the model will do very poorly and will have trouble predicting the target from new data. The parameters for the linear regression model was adjusted using Gradient Boosting. This helped increase the accuracy to 40%.

The accuracy of the KNN model without changing hyperparameters was 37%, this is the amount of variation that can be explained by the model's inputs or features. Adjusting to find the best k value slightly increased it's performance to 42% for the test set for a k value of 36. Accuracy with PCA decreased the model's ability to make predictions. Adjusting the model with GridSearchCV did not improve the model. The confusion matrix also showed an overall low correlation ability. It can successfully predict hospitals with no ratings and it has a better than average success of predicting hospitals with an average rating of 3. The random forest model caused overfitting, with an R2 value of about 87% for training set and 19% for test set. Using a loop to loop to review an unlimited about of max_depth values and then tuning again using n_estimators to tune the number of decision trees increased the R2 value from the previous model by a few percentages. A sequential model was also analyzed but was not a better model than the KNN model with the best k value of 36.

The best model evaluated was the KNN model with a k value of 36. A KNN model clusters data based on similar observations. The model's prediction is based on the distance of a particular data point to other similar data points. The model evaluated the appropriate number of clusters to come up with a best k value of 36. 


***Limitations & Next Steps:***

Other features not considered in the dataset may have a stronger correlation to a hospital's rating. Overall the KNN model with 36 k value does well in predicting 3 and 4 rated hospitals. This suggests that there is a trend to average and above average hospitals from the features evaluated in this dataset. However, there is a low correlation of all other ratings.


***For Further Information:***

For any additional questions, please contact abate.senait@gmail.com
