# SC1015 Mini Project
Lab group: ECDS1\
Team 3

Members:
Ryan Tang Shi Jie\
Lin RuiJun\
Sean Tongvanikkul

---
This repository contains all the Jupyter Notebooks, datasets, images, video presentations, and the source materials/references used and created as part of the Mini Project for SC1015: Introduction to Data Science and AI.

This README briefly highlights what we have accomplished in this project. If you want a more detailed explanation of things, please refer to the the Jupyter Notebooks in this repository. They contain more in-depth descriptions and smaller details which are not mentioned here in the README. For convenience, we have divided the notebooks into 3 parts which broadly relate to the 5 main sections of this project.

---
## Table of Contents:
1. Problem Formulation
2. Data Preparation and Cleaning
3. Exploratory Data Analysis
4. Machine Learning
5. Data Driven Insights and Conclusion

---
### 1. Problem Formulation

**Our Dataset:** [Resale flat prices based on registration date from Jan-2017 onwards](https://www.kaggle.com/aitzaz/stack-overflow-developer-survey-2020](https://beta.data.gov.sg/collections/189/datasets/d_8b84c4ee58e3cfc0ece0d773c8ca6abc/view)) \
**Our Question:** 

define any terms

**Rationale:**  

### 2. [Data Cleaning and Preparation](https://github.com/Stongvan/SC1015-ECDS1Team3/blob/524d312b345effc458397f36ce432c30712e7519/1.%20Data%20cleaning%20and%20preparation.ipynb)
In this section of the project, we prepped and cleaned the dataset to help us analyze our data better and also to help us use our data for the purposes of machine learning in the later sections. 

We performed the following:
1. **Convert variables to workable format:** converted variables such as `month` and `remaining_lease` to more workable formats
2. **Add coordinate data for addresses**: matched addresses with coordinate data
3. **Dropping NaNs, outliers and irrelevant columns**: All the `NaN` values and irrelevant columns were dropped, outliers were kept
4. **Creating new features:** created new variables such as `storey_midpoint`, `numeric_month`, `Distance_from_Centre (km)`, `distance_to_nearest_mrt` and `distance_to_nearest_mall`

### 3. [Exploratory Data Analysis](https://github.com/Stongvan/SC1015-ECDS1Team3/blob/46e4df2d399b31e9f18cf1f2fe80a6731e36f2db/2.%20Exploratory%20data%20analysis.ipynb)
Then, we explored our DataFrames further using Exploratory Data Analysis to answer questions like are there any patterns we are noticing? What do our variables look like?bAre there any underlying relationships between them? Can we make any inferences for our question at this stage? 

To achieve this we did the following:
1. **Explored numeric variables**: elab
2. **Explored categorical variables:** elab

For further findings and explanations, please refer to the Jupyter Notebook on EDA.

### 4. [Machine Learning Techniques](https://github.com/Stongvan/SC1015-ECDS1Team3/blob/46e4df2d399b31e9f18cf1f2fe80a6731e36f2db/2.%20Exploratory%20data%20analysis.ipynb)
Here, we then used a wide variety of machine learning models, including 
1. Multivariate linear regression
2. Random forest regressor
3. K-nearest neighbour.

We compared different models in order to find the one most suited to model the data. The metrics that we used to compared the model was r^2 and mean squared error.

We also created a function that takes in user input to predict resale prices. Users have to key in postal code, which will be converted to latitude and longitude, floor area sqm, remaining lease, storey, year, month and room type. The model is able to predict resale prices in the future as well due to the inclusion of year and month. 

### 5. [Exploratory Data Analysis](https://github.com/Stongvan/SC1015-ECDS1Team3/blob/46e4df2d399b31e9f18cf1f2fe80a6731e36f2db/2.%20Exploratory%20data%20analysis.ipynb)
Then, we explored our DataFrames further using Exploratory Data Analysis to answer questions like are there any patterns we are noticing? What do our variables look like?bAre there any underlying relationships between them? Can we make any inferences for our question at this stage? 

To achieve this we did the following:
1. **Explored numeric variables**: elab
2. **Explored categorical variables:** elab

For further findings and explanations, please refer to the Jupyter Notebook on EDA.
