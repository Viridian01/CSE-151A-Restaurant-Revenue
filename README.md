# CSE-151A-Restaurant-Revenue    🍽☕️🍻

## Jupyter Notebook
Gateway to Jupyter Notebook:
<a target="_blank" href="https://colab.research.google.com/github/Viridian01/CSE-151A-Restaurant-Revenue/blob/milestone4/main.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

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

## Introduction
<p style="margin-top: 20px;">&emsp; Do you ever wonder why some restaurants are more successful than others? Could it be the type of cuisine, consumer preferences, or menu prices? We hope to answer this question by developing a model that aims to predict our measure of success, and total revenue, utilizing many attributes about a restaurant. We chose this area of focus for a variety of reasons. First, the idea of predicting the success of an institution in the food sector immediately appeals to us as both a topic not heavily explored, as well as one that can personally affect us as consumers. Many of the applications of predictive machine learning models are in large companies and institutions, but restaurants can be locally owned, even by the people close to us. Furthermore, our dataset is clean and contains a large enough sample size with enough features, which are both vital aspects for training a performant model. Through this project, we hope not only to better understand the financial aspects of food but also to create a useful tool for small business owners to fine-tune their restaurants to maximize their revenue.</p>

## Data Exploration
We first introduce our dataset, with examples shown in [Table 1](#preprocessing). The full dataset can be found at this [URL](https://colab.research.google.com/github/Viridian01/CSE-151A-Restaurant-Revenue/blob/milestone4/main.ipynb). Our dataset has 8368 observations and 17 features (including the target, and revenue). The features are as follows:
   - `Name` — serves as an identifier for each restaurant.
   - `Location` — gives the location category of the restaurant, either rural, downtown, or suburban.
   - `Cuisine` — gives the type of cuisine the restaurant serves, either Japanese, Mexican, Italian, Indian, French, or American.
   - `Rating` — gives the average rating of the restaurant on a five-star scale.
   - `Seating Capacity` — gives the total number of seats in the restaurant.
   - `Average Meal Price` — gives the average price of a meal at the restaurant (in an unknown currency--we assume USD).
   - `Marketing Budget` — gives the budget allocated towards marketing by the restaurant (in an unknown unit--we assume USD per month).
   - `Social Media Followers` — gives the total number of followers on the restaurant's social media.
   - `Chef Experience Years` — gives the number of years of experience of the head chef.
   - `Number of Reviews` — gives the total number of reviews the restaurant has received.
   - `Avg Review Length` — gives the average length of a review (in an unknown unit--we assume words).
   - `Ambience Score` — gives the score of the restaurant's ambience on a 10-point scale.
   - `Service Quality Score` — gives the score of the restaurant's service on a 10-point scale.
   - `Parking Availability` — denotes whether parking is available at the restaurant or not.
   - `Weekend Reservations` — gives the number of total weekend reservations in an average week.
   - `Weekday Reservations` — gives the number of total weekday reservations in an average week.
   - `Revenue` — gives the total revenue generated by the restaurant (in an unknown unit--we assume USD per year).


## Preprocessing
Our dataset is already quite clean, so little preprocessing is required. Notably, our dataset contains no missing data, so imputation is not required. Our only preprocessing steps are the following:
   1. We encode the categorical features. For `Cuisine` and `Location`, we used One-Hot encoding. For `Parking Availability`, we simply encode it as 0 and 1, as the feature is a boolean value.

      | Name                      | Restaurant 0 | Restaurant 1 | Restaurant 2 |
      |---------------------------|--------------|--------------|--------------|
      | Location                  | Rural        | Downtown     | Rural        |
      | Cuisine                   | Japanese     | Mexican      | Italian      |
      | Rating                    | 4.0          | 3.2          | 4.7          |
      | Seating Capacity          | 38           | 76           | 48           |
      | Average Meal Price        | 73.98        | 28.11        | 48.29        |
      | Marketing Budget          | 2224         | 4416         | 2796         |
      | Social Media Followers    | 23406        | 42741        | 37285        |
      | Chef Experience Years     | 13           | 8            | 18           |
      | Number of Reviews         | 185          | 533          | 853          |
      | Avg Review Length         | 161.92       | 148.76       | 56.85        |
      | Ambience Score            | 1.3          | 2.6          | 5.3          |
      | Service Quality Score     | 7.0          | 3.4          | 6.7          |
      | Parking Availability      | Yes          | Yes          | No           |
      | Weekend Reservations      | 13           | 48           | 27           |
      | Weekday Reservations      | 4            | 6            | 14           |
      | Revenue                   | 638945       | 490208       | 541369       |
      
      _Table 1: The table shows the first 3 examples in the dataset, along with all of their features._

   2. We scale the data, using min-max normalization. Our data exploration shows that many of the features are not normally distributed, so this kind of scaling is more logical than standardization.

Our data exploration also shows that many features are already very linearly correlated with `Revenue`, so we do not feel the need to expand our feature set any further. Finally, we split our dataset into a training and testing subset.
 
## Model Selection
- After preprocessing, we tried a variety of different models without any tuning to see how they perform on the dataset. Specifically, we use linear regression, a decision tree, a random forest, K-Nearest Neighbors, SVM, and Neural Networks. Out of these (without tuning), the **random forest** performed the best, so we attempted to tune its hyperparameters a bit.

## Conclusion
After training and evaluating our first model, we obtained an RMSE of about \$42000 on the training set and about \$65000 on the testing set. For reference, the mean revenue across the dataset is about \$656000, so our first model already gives predictions generally about 10% away from the actual revenue. Since our model's training performance is a bit better than its testing performance, it is likely slightly overfitting the training data. Though we could theoretically spend more time tuning it with more hyperparameters, we've already seen in the grid search that the hyperparameters do not seem to have much effect on the results. Thus, we can either try considering simpler models (i.e., tuning the ones we've already looked at), or using a neural network. For variety, we will try a fully-connected neural network (MLP), which we can more thoroughly tune.
