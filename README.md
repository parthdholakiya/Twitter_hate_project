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

Since we have used TF-IDF tokenizer, Tf IDf can not handle out of vocablary words(OOV).TL-IDF: Term Frequency-Inverse Document Frequency (td-idf) is a powerful and useful tool, but it has drawbacks that cause it to assign low values to words that are relatively important, to be overly sensitive on the extensive margin, and to be overly resistant on the intensive margin. To overcome this issue, implement Facebook FastText 

![image](https://user-images.githubusercontent.com/94167271/210103669-08c4ffbd-4562-47c6-b0c9-18b05861c0f1.png)




FastText is an open-source, free, lightweight library that allows users to learn text representations and text classifiers.

Train a fasttext model, it expects labels to be specified with __label__ prefix. We will just create a third column in the dataframe that has __label__ as well as the Tweets

 
Pre-processing

  Remove punctuation
  
  Remove extra space
  
  Make the entire sentence lower case 
  
#### After cleaning and preprocessing Tweets data
  
"__label__none_hate user user thanks for lyft credit i can't use cause they don't offer wheelchair vans in pdx disapointed getthanked"

'__label__none_hate bihday your majesty'

'__label__none_hate factsguide society now motivation'

### After training model  precision and recall respectively are getting around 96%

![Screenshot (iknpono](https://user-images.githubusercontent.com/94167271/210107645-b0efe9ae-67d9-4bbc-b839-e417a2fec816.png)


****Prediction on FastText****

![FastText val1](https://user-images.githubusercontent.com/94167271/210106374-611ba325-086a-4a07-815b-5e5630bde18a.png)



 #### Install the Required Libraries
 
    !pip install transformers
    !pip install datasets
    !pip install numpy
    !pip install pandas



#### HuggingFace requires the data to be as Dataset Dictionary


DatasetDict({
    train: Dataset({
        features: ['Unnamed: 0', 'label', 'tweet'],
        num_rows: 25569
    })
    test: Dataset({
        features: ['Unnamed: 0', 'label', 'tweet'],
        num_rows: 6393
    })
})


#### Model training

Epoch	 Training Loss	Validation Loss	   Accuracy
1 	    0.131400	    0.168935	         0.964649
2	      0.096700	    0.156363	         0.968090
3	      0.039100	    0.164177	         0.969185
