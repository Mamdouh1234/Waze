# Waze
A Machine Learning predictive model for identifying Waze Navigation app Churn customers

## Overview 

Waze is a navigational app that aims to help users reach places more easier by identifying best routes for most places. Waze is facing some troubles and is thinking about churn customers , so they decided to model ad implement a Machine learning predictive model to help them identify Churn customers before they churn ,so that they could have a chance to retain those customers.
Two algorithms were built:
 - RandomForest
 - XGBOOST

the champion model was XGBOOST with F1-score 0.851 on the validation set , however it scored slightly low on the testinig set with F1-score 0.302

## Business Understanding 

Waze’s free navigation app makes it easier for drivers around the world to get to where they want to go. Waze’s community of map editors, beta testers, translators, partners, and users helps make each drive better and safer. Waze partners with cities, transportation authorities, broadcasters, businesses, and first responders to help as many people as possible travel more efficiently and safely.

The purpose of this project is to help prevent user churn on the Waze app. Churn quantifies the number of users who have uninstalled the Waze app or stopped using the app, on the other hand High retention rates indicate satisfied users who repeatedly use the Waze app over time.

Developing a churn prediction model will help prevent churn, improve user retention, and grow Waze’s business. An accurate model can also help identify specific factors that contribute to churn and answer questions such as:

Who are the users most likely to churn?

Why do users churn?

When do users churn?

## Data Understanding

The data consisted of approximately 15000 rows and 13 features(Before Feature Engineering). The features included information on customers trips such as: 
- sessions                                
- drives                      
- total_sessions            
- n_days_after_onboarding          
- driven_km_drives                   
- duration_minutes_drives
- label (Target Variable)                    
and more

## Modeling and Evaluation 

We trained two models which are:
 - RandomForest
 - XGBOOST

Cross Validation technique was applied , the dataset was splitted to 70% for training , 15% for validation and 15% for unseen testing data which will be used to evaluate our champion model.
   
considering accuracy measures , for each model , we output a confusion matrix and four accuracy measures , they are
 - Accuracy
 - Precision
 - Recall
 - F1 Score
   
Considering the given Scenario: 
- False positives: Waze may take proactive measures to retain users who are NOT likely to churn. This may lead to an annoying or negative experience for loyal users of the app.
- False negatives: Waze will fail to take proactive measures to retain users who are likely to stop using the app. For example, Waze might proactively push an app notification to users, or send a survey to better understand user dissatisfaction.

False positives will cost Waze huge ammount of money and time to regain employees through notifications , adverising , marketing campaigns and more

False negatives is also very dangerous as it will lead to churn customers without being identified.

**Both False positive and False Negative costs are high , so we will evaluate the model based on a balance between both of them , which is F1-score**

The champion model was **XGBOOST** with F1-score 0.851 on the validation set.

The model Scored 0.302 on the unseen testing set which is quite low.

## Conclusion

- RandomForest and XGBOOST were used for modeling , however XGBOOST scored higher than RandomForest on the validation set.


- XGBOOST didn't score as high as it should be on the unseen test set , it scored F1-score 0.302 which seems to be low , so we cannot implement this model at this stage , we should perform other rounds with different tests to improve the accuracy.


- Upon investigating the feature importance for the champion model, we find that 14 out of 18 features are important to be used when training the model , this opens a way to try another round to train the champion model using the most important features.


- Engineering more features , trying other algorithms and performing more advanced EDA might improve the model accuracy
