# Classifying Tweets

- Darryn Johnson
- Instructor : Mark Barbour
- Date : 10/19/2024
- Blog :
- Link to repository : 

## Overview

In this repository, we look into a dataframe containing 9,093 entries and 3 columns. Each row represents a tweet, who the tweet is directed to and the emotion assigned to that tweet. The emotion tags were crowd sourced from individuals who signed up to do this process. Some tweets were labeld as neutral, negative or positve. A small amount were labeld as unknown, these tweets where removed for the process of this model. The original data is from [Brands and Products emotions](https://data.world/crowdflower/brands-and-product-emotions)

## Business understaning 

There are 2 companies these tweets are directed to. Google and Apple. These tweets either are to the company directly, or the products they manufacture and sell. The purpose of this notebook is for a campany (in this case apple or google) to be able to classify tweets directed to them, and be able to consider the feedback the tweet may contain. In this case, That would be the negative tweets. The positve tweets still contain valuable information, as this tells them what they are doing right, but the negative feedback gives the most information.

 ## Data Distribution

 ![Screenshot 2024-10-16 124458](https://github.com/user-attachments/assets/5d9dd2f6-462d-4deb-b3dd-8821a2c29318)

Here we see the distribution of the emotions in the data. We can clearly see a balance issue, with negative having a very small amount when compared to the positive and neutral classes. While this is generally good for the company, this does pose an issue for the modeling process. This issue is handled in the notebook.

## Modeling 

After the pre processing needed for the model to function properly, the actualy modeling phase itself was failry straight forward. MultinomialNB was chosen as the primeary model. This was chosen simply because the model is very easy to use, and it works very well for what we are trying to do. This model was build upon by testing several way to handle the class imbalance, using SMOTE and RandomUnderSampler. RandomUnderSampler was chosen to be what the model was trained on as it showd tne best results for the metric we were mostly concerned about, which is precision. 

## Evaluation 

To evaluate the success of a model, we will be using specific type of metric - precision. Precision is a metric associated with false positives. False positives was chosen to be the metric to evaluate by because of what we want to model to do, that being classify emotion. To understand the logic behind this, lets dive into confusion metrices and evaluation metrics. Confusion metrices output a plot that shows the true negatives, true positives, false negatives and false positives that a given model made. Each of the metrics has a certain implication. True positives and true negatives are of course what we want the model to have the highest number of predictions in. But no model is perfect. A false negative means the model predicted the feature to be negative, when it was actually positive. In the case of this model, for example, it means it labeled a feature incorrectly, a positive emotion text as a negative one. While this isn't optimal, a more important metric to look at is the opposite, a negative emotion thought to be a positive one. This tweet will most likely never be looked at or analyzed because we think its good, when we're mostly interested in fixing the negatives at this time. To finally test the model, we used train_test_split as our validation approach. This splits the data in a way that allows a model to be built on a subset of the data, and tested on another subset of data that has never been seen by the model.

# Conclusion 

MultinomialNB functioned well for predicting emotions associated with the tweets. Some preprocessing was used to ensure the sucess of the model, and in the ned, the model reached an 86% precision rate.

## Repository Structure

```
├── .gitignore
├── README.md
├── classifying_tweets.ipynb
└── nlp_presentation.pdf
```
