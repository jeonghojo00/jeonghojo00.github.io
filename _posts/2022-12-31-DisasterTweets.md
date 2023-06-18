---
layout: post
title: 'Disaster Tweets'
date: 2022-12-31 00:00:00 -0500
categories: [machine learning, classification]
tags: [machine learning, data analytics, classification, imbalanced dataset, nlp, logistic regression, kaggle]
---

# Disaster Tweets Classification
[Code](https://https://github.com/jeonghojo00/MachineLearning/blob/main/Classification/Disaster_Tweets_Classification.ipynb)

## Description
This project was initiated by [Kaggle](https://www.kaggle.com/competitions/nlp-getting-started) to get started with Natural Language Processing.

Twitter has become an important communication channel in times of emergency. Since how people use words metaphorically is different from common definition of the word, we try to classify tweets by developing a natural lanauge processing model.

## Data Analysis
### 1. Label Distribution (Dataset Balance)
![Label Distribution](/assets/images/disaster_tweets/disastertweets_label_distribution.jpg)
- The labels are about balanced by 57:43 ratio.
### 2. Word Counts
![Word Counts](/assets/images/disaster_tweets/disastertweets_word_counts.jpg)
- It shows that the number of words in a tweet is pretty much normally distributed.

### 3. Word Clouds
- Before Cleaning
![Word Cloud](/assets/images/disaster_tweets/disastertweets_word_cloud.jpg)
- After Cleaning
![Word Cloud cleaned](/assets/images/disaster_tweets/disastertweets_word_cloud_cleaned.jpg)

- Cleanings
    - Removal of square brackets, hyperlink, and stopwords
    - Replacement of contractions
- Some words in the word cloud for disaster tweets, such as 'suicide bomber', 'hiroshima', 'area', 'storm', and 'flood', suggest a potential association with actual disaster events. On the other hand, the word cloud for non-disaster tweets includes words like 'going', 'want', and 'time', which may indicate more general or casual conversation topics.

## Model development and result 
- Tweet texts were tokenized
- Evaluation metrics are 'f1' and 'roc_auc" since they are good to improve False Negative to get more actual disaster tweet. 

- Model consideration
    - Common ML approach
        - Vectorize using TfidfVectorizer 
            - TfidfVectorizer is to penalize the commonly occurred words
        - ML models
            - Decision Tree, Logistic Regression, KNN, and Naive Bayes were tested but did not produce great performance
    - Transformer model
        - AutoModelForSequenceClassification, loaded from Huggingface API, was used.

- Result
![Model result](/assets/images/disaster_tweets/disastertweets_result.jpg)
- Since the accuracy recall is relatively small(0.78) while accuracy is about 0.82 and auc_roc is about 0.88, it indicates that it show less power in lowering False Negative. But it can be used as reference since auc_roc is about 0.88.

- Suggestion
1. More informatino about users such as location, tweet time, and picture analysis can be done.



