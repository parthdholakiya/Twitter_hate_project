# Twitter Hate Speech Detection using Hugging Face BERT Fine-Tuning

## Overview

This project addresses hate speech on Twitter using Hugging Face's BERT model, a powerful tool for natural language understanding. The goal is to fine-tune the model for hate speech detection in the informal and unstructured nature of tweets.

## Project Components

# BERT Fine-Tuning
## Dataset Preparation: 

Create a labeled dataset of tweets containing or not containing hate speech.
## Fine-Tuning:

Utilize the Hugging Face transformers library to fine-tune a pre-trained BERT model for text classification.
## Model Evaluation: 

Assess the model's performance on a test set to gauge its effectiveness in hate speech detection.
## Real-time Predictions: 

Leverage Hugging Face's pipelines for quick predictions in real-world scenarios.

## Getting Started

## 1 Install Dependencies:
    pip install transformers datasets numpy pandas
## 2 Load and Tokenize Dataset:
    from transformers import AutoTokenizer
    tokenizer = AutoTokenizer.from_pretrained("bert-base-uncased")
## 3 Train the Model: 
    from transformers import AutoModelForSequenceClassification, TrainingArguments, Trainer
    
    model = AutoModelForSequenceClassification.from_pretrained("bert-base-uncased", num_labels=2) 
## 4 Save the Model:
    model.save_pretrained("path/to/save/model")
    
## 5 Run Predictions:
    from transformers import pipeline
    
    classifier = pipeline("text-classification", model="path/to/saved/model", tokenizer="path/to/saved/tokenizer")

## Example Inferences
    data = ["Even the darkest night will end, and the sun will rise."]
    # Output: [{'label': 'non hate', 'score': 0.99}]
    
    data = ["tweet78 @user hey, white people: you can call people 'white' by @user  #race  #identity #med…"]
    # Output: [{'label': 'hate', 'score': 0.98}]

## Considerations

Ensure a diverse dataset for fine-tuning and be mindful of potential biases. In conclusion, using BERT for hate speech detection on Twitter proves powerful, providing an accurate tool to identify hate speech effectively
