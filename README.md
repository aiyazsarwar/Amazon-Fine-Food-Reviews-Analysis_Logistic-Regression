# Amazon-Fine-Food-Reviews-Analysis_Logistic-Regression
Amazon Fine Food Reviews Analysis Data Source: https://www.kaggle.com/snap/amazon-fine-food-reviews  EDA: https://nycdatascience.com/blog/student-works/amazon-fine-foods-visualization/  

The Amazon Fine Food Reviews dataset consists of reviews of fine foods from Amazon.  
Number of reviews: 568,454 
Number of users: 256,059 
Number of products: 74,258 
Timespan: Oct 1999 - Oct 2012 
Number of Attributes/Columns in data: 10  
Attribute Information:  
Id ProductId - unique identifier for the product 
UserId - unqiue identifier for the user ProfileName 
HelpfulnessNumerator - number of users who found the review helpful 
HelpfulnessDenominator - number of users who indicated whether they found the review helpful or not 
Score - rating between 1 and 5 
Time - timestamp for the review 
Summary - brief summary of the review 
Text - text of the review 

Objective: 

Given a review, determine whether the review is positive (rating of 4 or 5) or negative (rating of 1 or 2).   
[Q] How to determine if a review is positive or negative?  
[Ans] We could use Score/Rating. A rating of 4 or 5 can be cosnidered as a positive review. A rating of 1 or 2 can be considered as negative one. A review of rating 3 is considered nuetral and such reviews are ignored from our analysis. This is an approximate and proxy way of determining the polarity (positivity/negativity) of a review.

My Contribution to the project :

Apply Logistic Regression on these feature sets
SET 1:Review text, preprocessed one converted into vectors using (BOW)
SET 2:Review text, preprocessed one converted into vectors using (TFIDF)
SET 3:Review text, preprocessed one converted into vectors using (AVG W2v)
SET 4:Review text, preprocessed one converted into vectors using (TFIDF W2v)

Hyper paramter tuning (find best hyper parameters corresponding the algorithm that you choose)
Find the best hyper parameter which will give the maximum AUC value
Find the best hyper paramter using k-fold cross validation or simple cross validation data
Use gridsearch cv or randomsearch cv or you can also write your own for loops to do this task of hyperparameter tuning

Pertubation Test

Get the weights W after fit your model with the data X i.e Train data.

Add a noise to the X (X' = X + e) and get the new data set X' (if X is a sparse matrix, X.data+=e)

Fit the model again on data X' and get the weights W'

Add a small eps value(to eliminate the divisible by zero error) to W and W’ i.e W=W+10^-6 and W’ = W’+10^-6

Now find the % change between W and W' (| (W-W') / (W) |)*100)

Calculate the 0th, 10th, 20th, 30th, ...100th percentiles, and observe any sudden rise in the values of percentage_change_vector
Ex: consider your 99th percentile is 1.3 and your 100th percentiles are 34.6, there is sudden rise from 1.3 to 34.6, now calculate the 99.1, 99.2, 99.3,..., 100th percentile values and get the proper value after which there is sudden rise the values, assume it is 2.5
Print the feature names whose % change is more than a threshold x(in our example it's 2.5)

Sparsity
Calculate sparsity on weight vector obtained after using L1 regularization

NOTE: Do sparsity and multicollinearity for any one of the vectorizers. Bow or tf-idf is recommended.

Feature importance
Get top 10 important features for both positive and negative classes separately.

Feature engineering
To increase the performance of your model, you can also experiment with with feature engineering like :
Taking length of reviews as another feature.
Considering some features from review summary as well.

Representation of results
You need to plot the performance of model both on train data and cross validation data for each hyper parameter, like shown in the figure.
Once after you found the best hyper parameter, you need to train your model with it, and find the AUC on test data and plot the ROC curve on both train and test.
Along with plotting ROC curve, you need to print the confusion matrix with predicted and original labels of test data points. Please visualize your confusion matrices using seaborn heatmaps.

Conclusion
You need to summarize the results at the end of the notebook, summarize it in the table format. To print out a table please refer to this prettytable library link
Note: Data Leakage
There will be an issue of data-leakage if you vectorize the entire data and then split it into train/cv/test.
To avoid the issue of data-leakag, make sure to split your data first and then vectorize it.
While vectorizing your data, apply the method fit_transform() on you train data, and apply the method transform() on cv/test data.
For more details please go through this link.
