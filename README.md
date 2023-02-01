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

linl for tf idf https://www.youtube.com/watch?v=vZAXpvHhQow

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

#### (2) FastText

![image](https://user-images.githubusercontent.com/94167271/210103669-08c4ffbd-4562-47c6-b0c9-18b05861c0f1.png)

FastText is an open-source, free, lightweight library that allows users to learn text representations and text classifiers.

fastText provides two models for computing word representations: skipgram and cbow ('continuous-bag-of-words'). The skipgram model learns to predict a target word thanks to a nearby word. On the other hand, the cbow model predicts the target word according to its context.


![image](https://user-images.githubusercontent.com/94167271/216078560-ce7d47f8-238a-42be-89af-69d94a3d4732.png)

![image](https://user-images.githubusercontent.com/94167271/216078092-27405027-c55f-416b-8047-11db9e88218f.png)

Train a fasttext model, it expects labels to be specified with __label__ prefix. We will just create a third column in the dataframe that has __label__ as well as the Tweets

 
#### After performing Pre-processing steps like Remove punctuation, remove extra space, Make the entire sentence lower case tweets data looks like this.
  
"__label__none_hate user user thanks for lyft credit i can't use cause they don't offer wheelchair vans in pdx disapointed getthanked"

'__label__none_hate bihday your majesty'

'__label__none_hate factsguide society now motivation'

### After training model  precision and recall are getting around 96%

![Screenshot (iknpono](https://user-images.githubusercontent.com/94167271/210107645-b0efe9ae-67d9-4bbc-b839-e417a2fec816.png)


****Prediction on FastText****

![FastText val1](https://user-images.githubusercontent.com/94167271/210106374-611ba325-086a-4a07-815b-5e5630bde18a.png)


FastText model predicted well. Fasttext uses N_grams which is separate single words into N_number of words like N_gram=2 Then word=” COLD” became ("CO","OL","LD") so if in Real world model gets word like similar to these words the model will calculate cosine similarity between the words. which solves out of vocabulary (OOV) problem as certain level. To solve Out of vocabulary we need to use state of the art BERT model.

#### (3) Bert-Hugging Face 

![image](https://user-images.githubusercontent.com/94167271/216076283-fbbbe926-18f5-4511-9874-7b86041489ef.png)


![image](https://user-images.githubusercontent.com/94167271/212979447-67b2c8bd-070f-4de0-83b7-27f59d756f94.png)

BERT, which stands for Bidirectional Encoder Representations from Transformers, is based on Transformers, a deep learning model in which every output element is connected to every input element, and the weightings between them are dynamically calculated based upon their connection. When an unseen word is presented to BERT, it will be sliced into multiple subwords, even reaching character subwords if needed. That is how it deals with unseen(OOV) words.


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

![image](https://user-images.githubusercontent.com/94167271/216073219-f3445341-aa68-4548-8a48-1f55abc29acd.png)

#### Training on Bert: Model reach accuracy at 96 %

![Screenshot 44444555](https://user-images.githubusercontent.com/94167271/210153566-090bc95a-61e5-4e39-aa01-da56d41bb5f1.png)
  
#### Validate Bert model by testing on Tweets

![Screenshot (h](https://user-images.githubusercontent.com/94167271/210153323-5b6e683f-7367-4869-9c2e-cd405e2b36af.png)



