# Twitter_hate_project
Using NLP and ML, make a model to identify hate speech (racist or sexist tweets) in Twitter.

![download (1)](https://user-images.githubusercontent.com/94167271/189394381-23b1e157-81ae-453d-b9d4-b41212975d8c.png)

Problem Statement:  

Twitter is the biggest platform where anybody and everybody can have their views heard. Some of these voices spread hate and negativity. Twitter is wary of its platform being used as a medium  to spread hate. 

help Twitter in identifying the tweets with hate speech and removing them from the platform. You will use NLP techniques, perform specific cleanup for tweets data, and make a robust model.

Domain: Social Media

Analysis to be done: Clean up tweets and build a classification model by using NLP techniques, cleanup specific for tweets data, regularization and hyperparameter tuning using stratified k-fold and cross validation to get the best model.


after performing necessary data cleaning like---

--- Normalize the casing.

--- Using regular expressions, remove user handles. These begin with '@’.

--- Using regular expressions, remove URLs.

--- Using TweetTokenizer from NLTK, tokenize the tweets into individual terms.

--- Remove stop words.

--- Remove redundant terms like ‘amp’, ‘rt’, etc.

--- Remove ‘#’ symbols from the tweet while retaining the term.

TF-IDF values for the terms as a feature to get into a vector space model.

Model building: Ordinary Logistic Regression, Adjusting the class imbalance, Regularization and Hyperparameter tuning applying best parameters on test dataset got F1 score of 0.99.


                    precision    recall  f1-score   support

                 0       1.00      0.98      0.99      7451
                 1       0.75      1.00      0.86       540

          accuracy                           0.98      7991
         macro avg       0.87      0.99      0.92      7991
      weighted avg       0.98      0.98      0.98      7991



confusion_matrix

![image](https://user-images.githubusercontent.com/94167271/189967508-5a85797c-29ac-4afd-ad93-861c19f79878.png)


