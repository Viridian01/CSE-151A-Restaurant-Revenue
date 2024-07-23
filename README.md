# CSE-151A-Restaurant-Revenue    🍽☕️🍻

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

- After preprocessing, we tried a variety of different models without any tuning to see how they perform on the dataset. Specifically, we use linear regression, a decision tree, a random forest, K-Nearest Neighbors, and an SVM. Out of these (without tuning), the random forest performed the best, so we attempted to tune its hyperparameters a bit.

Here is the [link](https://colab.research.google.com/github/Viridian01/CSE-151A-Restaurant-Revenue/blob/main/main.ipynb) to our data exploration.

---
