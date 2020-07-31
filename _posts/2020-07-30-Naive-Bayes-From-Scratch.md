---
layout: post
title: Writing Multinomial Naive Bayes From Scratch
subtitle: Using only NumPy to create a Multinomial Naive Bayes in Python
image: https://github.com/JonNData/JonNData.github.io/blob/master/img/naive_title.jpg?raw=true
tags: [naive bayes, multinomial, data analysis, python, algorithm]
---
The Naive Bayes classifiers are a relatively simplistic group of statistical models for assigning class labels to a given input.
The predictions are based on comparing how likely the input would be observed in each class.  
  
  
![calendar](/img/naive_bayes.png)
This is Bayes Theorem and it states: the `probability of A given B` is equal to the quantity of the `probability of B given A`
times the `probability of A` divided by the `probability of B`.


A more intuitive way to understand this conditional probability is to use Bayesian terminology:
![bayesian-terminology](https://wikimedia.org/api/rest_v1/media/math/render/svg/d0d9f596ba491384422716b01dbe74472060d0d7)  
The `calculated probability` is equal to the `probability of the class` times the `probability of each input occurring in that class`.
Dividing by the `evidence` is included in the probability of each input occuring in that class.


The standard example given here is classifying email as `spam` or `non-spam`. The Naive Bayes model is supervised learning,
which means that it is trained on labeled data. Emails labeled as spam or non-spam are inputted into the Naive Bayes classifier, and the model calculates how much each word 
is associated with `spam` or `non-spam` based on frequency in each class.

There are 3 flavors of Naive Bayes classifiers: Bernoulli, Multinomial, and Gaussian. These correspond to the distribution of the features being analyzed. 
* Bernoulli distribution is binary, did X occur or not?
* Multinomial distribution is discrete, often the frequency or count of X.
* Gaussian distribution is also known as the normal distribution for continuous variable, could be a measurement like 88.2mL 

What's the `Naive` part of Naive Bayes?  
The naivete in this regard comes from assuming that all probabilities are independent. In the email example this means that the probability of finding the word "Timeshare"
isn't affected by seeing the words "Limited Offer". This is often and easily violated, especially in the context of natural language. However, despite the relatively simplistic model,
it produces good results.  

I will be coding from scratch a multinomial Naive Bayes classifier. The main goals are to able to fit it on documents with labels, and use it to predict labels on new inputs.  

I'll need to have several data preprocessing steps to handle text input into this model.
The first I will use to tokenize the document:
```
  def tokenize(self, document):
    """
    Take in a document and return a list of words
    """
    doc = document.lower()
    # remove non-alpha characters
    stop_chars = '''0123456789!()-[]{};:'"\,<>./?@#$%^&*_~'''
 
    tokens = ""
    # iterate through and make each token
    for char in doc:
      if char not in stop_chars:
        tokens += char
        
    return tokens.split() # now a list of tokens
 ```
 Tokenizing entails processing a document into a list of words, removing unwanted characters. Next I had to create a dictionary with the word counts per class.
 A key piece to writing this class was making sure you had access to `prior probabilities` for future usage in the overall theorem. 
 
 
