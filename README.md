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
4. Multivariate Linear Regression
5. Data Driven Insights?

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

### 3. [Exploratory Data Analysis](insertlink)
Then, we explored each of our two DataFrames further using Exploratory Data Analysis to answer questions like are there any patterns we are noticing? What do our success variables look like? What about the conventionality variables? Are there any underlying relationships between them? Can we make any inferences for our question at this stage? 

To achieve this we did the following:
1. **Explored `ConvertedComp`**: This variable is the annual compensation in USD (a.k.a Salary). Median of around $54k was seen. A lot of outliers with high salaries were present.
2. **Explored `JobSat`:** This variable is the job satisfaction (`0-4` scale). Most frequent ratings were `2` and `4`. The mean rating was at `2.3`.
3. **Explored Relationships Between `JobSat` and `ConvertedComp`:** Weak correlation was seen between `JobSat` and `ConvertedComp`.
4. **Explored Variables Related to Conventionality:** Studied which options in the `6` variables were more frequently selected by respondents. 

For further findings and explanations, please refer to the Jupyter Notebook on EDA.
