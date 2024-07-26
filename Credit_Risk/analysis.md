
## Overview of the Analysis


The purpose of this analysis is to build a model that can identify the creditworthiness of borrowers based on loan risk. The financial information was based on a dataset of historical lending activity from a peer-to-peer lending services company. The variable I was trying to predict was 'value_counts' or the number of  predicted loans by high-risk[1] or healthy[0]. 

The stages of the machine learning process I went through for this analysis was to read the CSV file into a Pandas Dataframe, spliting & separting the columns into training and testing datasets by using train_test_split. Then I created a logistic regression model with the origianl data using X_train and y_train then made a predicition using the testing data by using 

test_predictions = logistic_regression_model.predict(X_test)
pd.DataFrame({'Predictions': test_predictions, 'Actual': y_test}). 
I then prenting the testing_preditions and got 19384. 

For the results of the analysis I generated a confusion matrix and classification report for the model. 

## Results

Using bulleted lists, describe the accuracy scores and the precision and recall scores of all machine learning models.


- Confusion Matrix
    - The model shows that out of the 18,759 loan status's that are healthy, the model predicted 18,679  as healthy and 80 as healthy incorrectly.
    - The model also shows that out of the 625 high-risk loans, the model predicted 558 correctly and 67 as non-healthy incorrectly. 
    logistic_matrix = confusion_matrix(y_test, testing_predictions)
    print(logistic_matrix)
    [[18679    80]
    [   67   558]]

- Classification report
    - the logistic regression model predicted healthy loans 100% of the time and predicted non-healthy loans 87% of the time. 
    - the recall scores show that the model made 0% of mistakes when predicting healthy loans and made 11% of mistakes when predicting non-healthy loans. 

    logistic_classreport = classification_report(y_test, testing_predictions)
    print(logistic_classreport)
                precision    recall  f1-score   support

            0       1.00      1.00      1.00     18759
            1       0.87      0.89      0.88       625

        accuracy                           0.99     19384
    macro avg       0.94      0.94      0.94     19384
    weighted avg       0.99      0.99      0.99     19384

## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. 
* Which one seems to perform best? How do you know it performs best?
- The logistic regression classification report performed better than the confusion matrix due to the classification report having weighted averages and macro averages. 
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )
- It's more important to predict the high-risk loans since failure to do so can result in accessive losses in sales if not correctly predicted. Although it is important to be able to predict successful loans since a false prediction leading to a denial of a healthy loan can result in a loss of revenue. 