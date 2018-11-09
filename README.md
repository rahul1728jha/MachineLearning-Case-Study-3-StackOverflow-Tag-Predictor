# MachineLearning-Case-Study-3-StackOverflow-Tag-Predictor

# Business Problem 
Stack Overflow is the largest, most trusted online community for developers to learn, share their programming knowledge, and build their careers.

Stack Overflow is something which every programmer use one way or another. Each month, over 50 million developers come to Stack Overflow to learn, share their knowledge, and build their careers. It features questions and answers on a wide range of topics in computer programming. The website serves as a platform for users to ask and answer questions, and, through membership and active participation, to vote questions and answers up or down and edit questions and answers in a fashion similar to a wiki or Digg. As of April 2014 Stack Overflow has over 4,000,000 registered users, and it exceeded 10,000,000 questions in late August 2015. Based on the type of tags assigned to questions, the top eight most discussed topics on the site are: Java, JavaScript, C#, PHP, Android, jQuery, Python and HTML.

# Problem Statemtent
Suggest the tags based on the content that was there in the question posted on Stackoverflow.

# Real World / Business Objectives and Constraints 
Predict as many tags as possible with high precision and recall.
Incorrect tags could impact customer experience on StackOverflow.
No strict latency constraints.

# Machine Learning problem 

# Data 
Data Field Explaination

Dataset contains 6,034,195 rows. The columns in the table are:

* Id - Unique identifier for each question
* Title - The question's title
* Body - The body of the question
* Tags - The tags associated with the question in a space-seperated format (all lowercase, should not contain tabs '\t' or ampersands '&')


# Performance metric 
Micro-Averaged F1-Score (Mean F Score) : The F1 score can be interpreted as a weighted average of the precision and recall, where an F1 score reaches its best value at 1 and worst score at 0. The relative contribution of precision and recall to the F1 score are equal. The formula for the F1 score is:

F1 = 2 (precision recall) / (precision + recall)

In the multi-class and multi-label case, this is the weighted average of the F1 score of each class. 

'Micro f1 score': 
Calculate metrics globally by counting the total true positives, false negatives and false positives. This is a better metric when we have class imbalance. 

'Macro f1 score': 
Calculate metrics for each label, and find their unweighted mean. This does not take label imbalance into account. 

https://www.kaggle.com/wiki/MeanFScore 
http://scikit-learn.org/stable/modules/generated/sklearn.metrics.f1_score.html 


# Data Preparation:
We split our data into train and test subsets using a 80-20 split.
We use tf-idf vectorizer to vectorize our questions(title+body). We also try out CountVectorizer but tf-idf vectorized features give better results

# Modeling:
We use Logistic Regression with OneVsRest Classifier.Since input data is high dimensional and we know that typically linear models work very well with high-dim data and is computationally very cheap, thus we choose LR as our final model. We tried with Lin SVM too but it gave almost similar results

# Conclusion:
Our best model was able to achieve a Mean F-score of > 0.5
