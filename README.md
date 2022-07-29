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

The target was overall rating. Overall rating is an ordinal feature on a scale of -1 to 5, -1 being no rating and 5 being the higest rated. For example, a rating of 3 means that the hospital rating is average and falls along the national average rating of most hospitals in the United States. A rating of 2 means that the hospital is below the national average rating. There were at least 4 other features related to various ratings and this was dropped from the dataset to prevent knowing too much about the target variable. Other features included quality of care, value, and costs of procedures due to heart heart attack, heart failure, pneumonia, and hip and knee surgery. After preprocessing, classification models such as logistic regression, KNN, and Random Forest Regressor were used and different hyperparameters and metrics were applied to increase the accuracy and performance of these models.


***Results:***


![image](https://user-images.githubusercontent.com/105686944/181847767-076ec175-b941-46db-8175-fe49132e84e8.png)

The Overal Rating histogram above shows that the greatest number of hospitals have a 3, or average, rating. Over a 1000 hospitals have a 4 rating but almost just as many have no rating.


![image](https://user-images.githubusercontent.com/105686944/181847811-9308a380-07d2-48d7-96be-52b71d74e6e6.png)

Heart failure costs are slightly higher than heart attack costs at 4 and 3 rated hospitals. Heart attack costs are higher than heart failure costs at 1 rated hospitals. In general, heart failure and heart attack costs decrease the higher the hospital rating.


![image](https://user-images.githubusercontent.com/105686944/181847839-7f277bcc-48f1-4cbe-af53-8d0c9557428b.png)

The trend in the above barplot shows the higher the hospital rating the lower the costs for pneumonia procedures while costs for hip and knee procedures fluctuate more with a average rating of 3 having the least cost.


![image](https://user-images.githubusercontent.com/105686944/181847859-81c7bd02-bbb4-422b-9441-a03a3a49e422.png)

1=below average. 2=average. 3=higher than average.
The above graph is a stripplot of hip and knee procedure costs and the type of facility based on the procedure's quality compared to the national average. Most hospitals no matter the type have a average rating of 2, which is average compared to the national average. There also appears to be a few more 1 rated, or below average rated government hospitals as compared to the others.



***Model:***

The accuracy of the KNN model without changing hyperparameters was 44.8%, this is the amount of variation that can be explained by the model's inputs or features. This reflects a very poor model. Adjusting to find the best k value slightly increased it's performance to 46% for the test set for a k value of 14. Accuracy with PCA decreased the model's ability to make predictions. The model can only explain 44.8% of the variance. The confusion matrix also showed an overall low correlation ability. It can successfully predict hospitals with no ratings and it has a better than average success of predicting hospitals with an average rating of 3.

The default logistic regression model had slightly more overfitting than the KNN model. It's training accuracy was 87.8% and test accuracy was 44.2%. The model was then tuned using L1 and L2 regularization. L1 regularization had it's highest accuracy at 0.1 which was about 46.5%. L2 regularization was the highest at 0.1 as well with 46.7%. This was better than the best tuned KNN model.

In the random forest model, I first tried tuning via loop to loop to review an unlimited about of max_depth values and then tuned again using n_estimators to tune the number of decision trees. The Random Forest model tuned with loop to loop had the highest test score at 52.5% with a max_depth of 10. This model also did better than the logistic regression and KNN models as well.

However, even the best performing model here was not very good. The accuracy of the model to predict a hospital's rating is just too low to be considered for production. In addition, the training accuracy scores tended to be a lot higher than the testing scores which is a sign of over-fitting. Overfitting is definitely an issue as it suggests the model has too much noise and will not be able to decipher new data in an efficient and accurate manner.


***Limitations & Next Steps:***

Other features not considered in the dataset may have a stronger correleation to a hospital's rating. There were also too many hospitals with no rating. The 0 rating can account for about 20-25% of the dataset.



***For Further Information:***

For any additional questions, please contact abate.senait@gmail.com
