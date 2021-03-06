# Healthcare Ticketing Topic Classification #
This repository hosts my code to classify phone call summaries in a healthcare provider.

## Introduction ##
The electronic medical record system at my workplace includes patient communication such as email and phone conversation notes. Office visit and ER visit records also cover detailed free-text physician's notes, in addition to the usual patient measures (body temperature, blood pressure readings, etc., which are structured). All these emails and notes are unstructured texts. Significant efforts have been made to extract relevant information, especially symptoms and diagnoses, from them. My initial interest in natural language processing was motivated by such efforts.  

One of the many approaches we can take is to categorize patient emails and phone call scripts. They are usually paragraph-long texts. To categorize such texts using machine learning algorithms before linking them to the patient's electronic chart will create a more complete picture of the patient's medical situation for the provider. For example, a patient could write to their primary care provider complaining about recurring skin rash; if such email were to be automatically categorized as "symptoms", added to the patient's problem list, then reviewed by the primary care provider at the time of the patient's next office visit, the primary care provider would likely be prompted to exam the patient for chronic dermatitis - without having to reply on the provider's memory of the original email. A provider's capability is greatly extended with such automated categorization of text. 

## Description ##
The analysis in this repository aims at achieving the abovementioned automated categorization. The dataset used in this analysis is provided by [Kaggle](https://www.kaggle.com/vinodkumarcvk/healthcareticketingsystem), where each instance consists of a summary of a phone call and a category of the call. The category is the target label. Each summary is tokenized before a word embedding is learned on them. Then I implement a simple multilayer perceptron neural network, a rudimentary recurrent neural network (RNN) with long short-term memory (LSTM) and a convolutional neural network (CNN).

## Future Work ##
A big word embedding size is known to lead to overfitting but "how big is big" varies with each dataset. Experimenting with different embedding sizes may help with my overfitting problem.

Also I would like to try pre-trained word embedding methods such as `word2vec` and Global Vectors for Word Representation (GloVe), instead of the one learned from the training data. Currently the RNN is not tuned due to its computational demand, but RNN is found to be sensitive to hyperparameters. I will start with a grid search of the batch size for RNN. I have also seen arguments that now is the time to drop RNN/LSTM - the go-to method for many NLP tasks for a few years - and use convolutional neural network (CNN) as they are easier to train or Residual neural network (ResNet) as they perform well for deep structures (e.g., with hundreds of layers). ~~I will train a CNN and compare its performance to RNN's.~~ CNN seems to have similar performance to RNN. Now my future work will be to train ResNet or ImageNet model on this dataset. 

## Requirements ## 
`Python`, `Keras`, and the common `Python` analytical packages. 