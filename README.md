# CSE-151A-Restaurant-Revenue    🍽☕️🍻

## Introduction

<p style="margin-top: 20px;">&emsp; Do you ever wonder why some restaurants are more successful than others? Could it be the type of cuisine, consumer preferences, or menu prices? We hope to answer this question by developing a model that aims to predict our measure of success, and total revenue, utilizing many attributes about a restaurant. We chose this area of focus for a variety of reasons. First, the idea of predicting the success of an institution in the food sector immediately appeals to us as both a topic not heavily explored, as well as one that can personally affect us as consumers. Many of the applications of predictive machine learning models are in large companies and institutions, but restaurants can be locally owned, even by the people close to us. Furthermore, our dataset is clean and contains a large enough sample size with enough features, which are both vital aspects for training a performant model. Through this project, we hope not only to better understand the financial aspects of food but also to create a useful tool for small business owners to fine-tune their restaurants to maximize their revenue.</p>

## Written Report
This is where you can find our written report on the project:
<a target="_blank" href="">
   <img src="https://img.shields.io/badge/Download%20as%20PDF-EF3939?style=flat&logo=adobeacrobatreader&logoColor=white&color=black&labelColor=ec1c24">
</a>


## Environment setup instructions:

1. Link to download data from [Kaggle](https://www.kaggle.com/datasets/anthonytherrien/restaurant-revenue-prediction-dataset) or [here](data/restaurant_data.csv)
2. Unzip the file and upload it into the Google Colab
3. Imports needed for data processing

   ```
   import numpy as np
   import pandas as pd
   import matplotlib.pyplot as plt
   import seaborn as sns
   ```
---
## Preprocessing

- As we started to explore our data, we found that our data was already quite clean, and the only two required steps were **scaling the data** and **encoding the categorical features**.
- **Scaling the data**
  - We used min-max normalization, as the data is not very normally distributed.
- **Encoding the categorical features**
  - We used one-hot encoding for Cuisine and Location to encode the categorical features. For Parking Availability, it made more sense to encode it simply as 0 and 1 because the feature is a boolean value.
 
## Model Selection

- After preprocessing, we tried a variety of different models without any tuning to see how they perform on the dataset. Specifically, we use linear regression, a decision tree, a random forest, K-Nearest Neighbors, SVM, and Neural Networks. Out of these (without tuning), the **random forest** performed the best, so we attempted to tune its hyperparameters a bit.

Gateway to Jupyter Notebook:
<a target="_blank" href="https://colab.research.google.com/github/Viridian01/CSE-151A-Restaurant-Revenue/blob/milestone4/main.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

## Conclusion

After training and evaluating our first model, we obtained an RMSE of about \$42000 on the training set and about \$65000 on the testing set. For reference, the mean revenue across the dataset is about \$656000, so our first model already gives predictions generally about 10% away from the actual revenue. Since our model's training performance is a bit better than its testing performance, it is likely slightly overfitting the training data. Though we could theoretically spend more time tuning it with more hyperparameters, we've already seen in the grid search that the hyperparameters do not seem to have much effect on the results. Thus, we can either try considering simpler models (i.e., tuning the ones we've already looked at), or using a neural network. For variety, we will try a fully-connected neural network (MLP), which we can more thoroughly tune.

---
