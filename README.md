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

- As we started to explore our data, we found that our data was already quite clean, and the only two required steps were **scaling the data**, **encoding the categorical features**, and **removing outliers**.
- **Scaling the data**
  - We used min-max normalization, as the data is not very normally distributed.
- **Encoding the categorical features**
  - We used one-hot encoding for Cuisine and Location to encode the categorical features. For Parking Availability, it made more sense to encode it simply as 0 and 1 because the feature is a boolean value.
-  **Removing Outliers**
   - To remove the outliers, we used log transformation.
 
## Regression Models

- With our data cleaned up, we created our first models, starting with a linear and polynomial model.

Here's the [link](https://colab.research.google.com/github/Viridian01/CSE-151A-Restaurant-Revenue/blob/main/main.ipynb) to our data exploration.

---
