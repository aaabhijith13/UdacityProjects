# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### Abhijith Anil Vamadev

## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
TODO: The train dataset has casual and registered columns that are not needed, as they are not in the test dataframe so they were dropped after the data was read. Also, as the data was read for both train and test the datetime, was parsed into datetime. 

### What was the top ranked model that performed?
TODO: WeightedEnsemble_L3 was the top ranked model.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
TODO: Datetime was split into year, month, day and hour. Looking at the values, year only has only 2011 and 2012 so it was conveerted into a binary column is_2011 which indicates 1 if it is 2011 and 0 if it is 2012. Similarly it as completed for test and then the datetime column was dropped from both train and test. Season and Weather was considered as categorical variables as they had 4 values within each, this was done to both train and test again. A count plot was completed to look at the categorical variables. Looking at it, Weather had 4 categorical values, but 4 only appeared once. So that was converted into 3 and weather now has 3 categorical variable instead of 4. 
Once that wwas completed for both train and test, the following columns 'temp', 'atemp', 'humidity', 'windspeed', 'hour', 'month', 'day' which was either integer or float was then standardized. And also dummy variables was added to the categorical variable "Season" and "winter". Once all the numerical variables were standardized and categorical variables had dummy variables it was then given for modelling. 

### How much better did your model preform after adding additional features and why do you think that is?
TODO: The model initally without any features had a score of 1.79038, but as more features was added the model got more and better information to make good inference on the data.Also,increasing the number of features can help reduce overfitting in the model.

## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
TODO: Model did not perform that significantly , but few points of change was observed. It was hard configuring AUtoGlouns WeightedEWnsemble_L3 model so much hyperparameterization could not be done. The hyperparameter kwaargs was also tuned which included the number of trials, and the searcher. Model did not improve any further with hyperparameter tuning.

### If you were given more time with this dataset, where do you think you would spend more time?
Ideally with more time, more visualization and EDA would be need to be explored for each of the variables and identify outliers and as well as look to do transformation on some of the numerical variables as they were heavily skewed. Also, running multiple different models wwould be good without relying entirely on AutoGluon. 
### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|initial|N/A|N/A|N/A|1.709|
|add_features|N/A|N/A|N/A|0.45882|
|hpo|num_boost_round|learning_rate|feature_fraction|0.54948|
			
### Create a line plot showing the top model score for the three (or more) training runs during the project.



![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.


![model_test_score.png](img/model_test_score.png)

## Summary
TODO: Overall, feature engineering and EDA was conducted on the data to explore how well could we predict the demand for bikes by using 2011 and part of 2012 data to predict the upcoming year sales. WeightedEWnsemble_L3 performed the best with 0.4853 score, hyperaparameter tuning the model did not help as it brought down the score to 0.53981. Additionally, for an aditional model XGboost with CV grid search was completed and it did not perform as well as any other models. Also, looking at the EDA it was observed that some of the columns have outliers and trasnforming the columns might yeild better results. Also, to be noted are that Atemp and temp columns were highly positively correlated which could indicate that they provide the same value and by removing one column better results could be yeilded. 
