# Subreddit Classifier

### Executive Summary  
Reddit has identified that they have lost the tags for 2 of their subreddits for a few days and they are **r/buildapc** and **r/Cooking**.  
Fortunately, there's a backup for the 2 subreddits. However, posts relating to the 2 subreddits during this period have had no classification. You have been tasked to classify the tagless posts into their correct subreddits with an appropriate model.  

This project aims to correctly classify the subreddits, and select a model after comparing the efficacy and limitations of two classification models.


### Contents:
- [Data Import and Cleaning](#Data-Import-and-Cleaning)
- [Natural Language Processing](#Natural-Language-Processing)
- [Exploratory Data Analysis](#Exploratory-Data-Analysis)
- [Logistic Regression](#Logistic-Regression)
- [Naive Bayes](#Naive-Bayes)
- [Conclusion](#Conclusion)

### Conclusion
Model scores:
- Logistic Regression = 0.9557
- Naive Bayes = 0.9758

Our Naive Bayes model performed better than our Logistic Regression and that it can successfully predict our classification of posts correctly at a 97.5% accuracy.

Logistic Regression makes a prediction for the probability using a direct functional form where as Naive Bayes figures out how the data was generated given the results. Therefore with a larger dataset Logistic Regression would perform better as it would have better probability tuned to the model vs Naive Bayes that is a generative model[1].