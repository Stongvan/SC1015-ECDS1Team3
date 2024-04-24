# SC1015 Mini Project - HDB Resale Prices
Lab group: ECDS1\
Team 3

Members:
Ryan Tang Shi Jie\
Lin RuiJun\
Sean Tongvanikkul

---
This repository contains all the Jupyter Notebooks, datasets, video presentations, and the source materials/references used and created as part of the Mini Project for SC1015: Introduction to Data Science and AI.

This README briefly highlights what we have accomplished in this project. If you want a more detailed explanation of things, please refer to the the Jupyter Notebooks in this repository. They contain more in-depth descriptions and smaller details which are not mentioned here in the README. 

---
## Table of Contents:
1. Problem Formulation
2. Data Preparation and Cleaning
3. Exploratory Data Analysis
4. Machine Learning Techniques
5. Data Driven Insights and Conclusion
6. References

---
### 1. Problem Formulation

**Our Dataset:** [Resale flat prices based on registration date from Jan-2017 onwards](https://www.kaggle.com/aitzaz/stack-overflow-developer-survey-2020](https://beta.data.gov.sg/collections/189/datasets/d_8b84c4ee58e3cfc0ece0d773c8ca6abc/view)) \
**Our Question:** How can we predict resale prices of HDB flats?

**Rationale:**  This is salient to us especially as Economics students, where housing is one of the key expenditures of households in Singapore. Understanding the factors that influence resale prices, as well as how to predict housing prices can give us more insight into the housing market and its broader implications.

Therefore, Data Science problem will be a numeric one, where we aim to predict resale prices using regression techniques.

**Unique Variables:**
1. Remaining Lease: All HDB flats have a 99-year lease, thus remaining lease tells us the "lifespan" of the flat. This differs from how in other countries, property usually appreciates with age. 

### 2. [Data Cleaning and Preparation](https://github.com/Stongvan/SC1015-ECDS1Team3/blob/524d312b345effc458397f36ce432c30712e7519/1.%20Data%20cleaning%20and%20preparation.ipynb)
In this section of the project, we prepped and cleaned the dataset to help us analyze our data better and also to help us use our data for the purposes of machine learning in the later sections. 

We performed the following:
1. **Convert variables to workable format:** converted variables such as `month` and `remaining_lease` to more workable formats
2. **Add coordinate data for addresses**: matched addresses with coordinate data
3. **Dropping NaNs, outliers and irrelevant columns**: All the `NaN` values and irrelevant columns were dropped, outliers were kept
4. **Creating new features:** created new variables such as `storey_midpoint`, `numeric_month`, `Distance_from_Centre (km)`, `distance_to_nearest_mrt` and `distance_to_nearest_mall` using a csv of the coordinates of every mrt and mall in Singapore. We used spatial indexing to query the nearest MRT and mall in the K dimmensional tree, and add in the distances to the nearest amenity into the dataframe to see if this will affect resale prices.

### 3. [Exploratory Data Analysis](https://github.com/Stongvan/SC1015-ECDS1Team3/blob/46e4df2d399b31e9f18cf1f2fe80a6731e36f2db/2.%20Exploratory%20data%20analysis.ipynb)
Then, we explored our DataFrames further using Exploratory Data Analysis to answer questions like are there any patterns we are noticing? What do our variables look like?bAre there any underlying relationships between them? Can we make any inferences for our question at this stage? 

To achieve this we did the following:
1. **Explored numeric variables**:
   - Around 2000 monthly transactions on average
   - Average resale price is around 500k.
   - We noticed that flats are on average 500m from both the nearest mall as well as MRT Station, which indicates the high connectivity in Singapore as well as the proximity to amenities
   - Flats are observed to be sold mostly with remaining leases of ~95y, 80y and 75y, with the first being the most frequent. This suggests that many owners sell their flats immediately after the 5 year Minimum Occupancy Period (MOP).

2. **Explored categorical variables:**
   - Most common transactions were on 4 room flats, might be popular as the space is suitable for families
   - Price in general increases with number of rooms

We then decided to use the following variables for our ML:

   `floor_area_sqm`: Size of the property in square meters.\
   `remaininglease`: Remaining lease duration of the property.\
   `latitude`: North-south position of the property on Earth.\
   `longitude`: East-west position of the property on Earth.\
   `storey_midpoint`: Midpoint of the property's storeys in a building.\
   `numerical_month`: Number of months from base period (January 2017), in order to capture the effects of time\
   `Distance_from_Centre (km)`: Distance of the property from the city center.\
   `distance_to_nearest_mrt`: Distance to the nearest Mass Rapid Transit (MRT) station.\
   `distance_to_nearest_mall`: Distance to the nearest shopping mall.\
   `numeric_room_type`: Type of rooms in the property represented numerically.

For further findings and explanations, please refer to the Jupyter Notebook on EDA.

### 4. [Machine Learning Techniques](https://github.com/Stongvan/SC1015-ECDS1Team3/blob/b96df413a0335f2de1a2dfdf896ce190e400868b/3.%20Machine%20Learning.ipynb)
Here, we then used a wide variety of machine learning models, including 
1. **Multivariate linear regression**\
Multivariate linear regression aims to model the relationship between multiple independent variables (features) and a dependent variable (resale price) by fitting a linear equation to observed data.

   Predicted Price ≈ 5,900,000
   
   Plus
   + 4300 * Floor Area (sqm)
   + 4200 * Remaining Lease
   + 5200 * Floor Number
   + 14000 * Room Type (numeric)
   + 2300 * Months from Base Period (Jan 2017)
     
   Minus
   - 460000 * Latitude 
   - 53000 * Longitude 
   - 16000 * Distance from Centre (km) 
   - 15 * Distance to Nearest MRT (m)
   - 9.7 * Distance to Nearest Mall (m) 

2. **Random forest regressor**\
Random Forest grows multiple decision trees which are merged together for a more accurate prediction. It uses averaging to improve the predictive accuracy and control over-fitting.

   Top 5 Feature Importances:\
   `distance_from_centre_km`: 22.94%\
   `floor_area_sqm`: 41.97%\
   `numerical_month`: 11.82%\
   `remaininglease`: 9.54%\
   `numeric_room_type`: 3.73%

3. **K-nearest neighbour**\
KNN is an instance-based learning algorithm that is used for regression tasks — predicting a continuous-valued attribute associated with an object. The model then matches it to the nearest flats that we have in our data set and try to predict the resale price for the new flat.

   Our model found 3 as the best n_neighbours 

We compared different models in order to find the one most suited to model the data. The metrics that we used to compared the model was r^2 and mean squared error. In our results, the random forest model actually resulted in the highest r^2 and lowest mean squared error. We thus decided to use this to model our function below.

We also created a function that takes in user input to predict resale prices. Users have to key in postal code, which will be converted to latitude and longitude, floor area sqm, remaining lease, storey, year, month and room type. The model is able to predict resale prices in the future as well due to the inclusion of year and month. However, this function tends to predict prices that are a little higher than the actual value, and it might be attributed to other factors which our model does not take into account such as economic factors and future developments in the region.

### 5. Data Driven Insights and Conclusions

**Key Factors Driving Resale Prices:**\
Floor Area & Remaining Lease: Larger floor areas and longer remaining lease durations positively impact resale prices.
Location Proximity: Properties closer to amenities like MRT stations and shopping malls command higher prices.
Temporal & Room Type Factors: Transactions closer to the base period and certain room configurations influence resale values.

**Model Recommendation:**\
Random Forest Regressor: Among evaluated models, the random forest regressor demonstrated superior performance, offering reliable predictions of resale prices.
Utilization in Decision-Making: Stakeholders can leverage this model for strategic decision-making regarding property investments, sales, and acquisitions.

**Predictive Function Usage:**\
Potential Resale Values: Prospective buyers/sellers can utilize the predictive function to estimate potential resale values, considering factors like location, floor area, and remaining lease.
Future Price Prediction: By inputting future dates, users can forecast resale prices, aiding in long-term planning and investment strategies.

**Considerations and Limitations:**\
Economic & Policy Factors: While the model provides valuable insights, it may not account for broader economic trends or policy changes impacting the housing market.
Continuous Monitoring: Regular updates and refinement of the model are essential to ensure accuracy and relevance amidst evolving market dynamics.

In summary, leveraging insights from our data-driven analysis, stakeholders can make informed decisions in the dynamic landscape of the HDB resale market, optimizing returns and mitigating risks in property transactions.

### 6. References

1. https://github.com/changjulian17/resale_HDB
2. https://garba.org/posts/2022/knn/
3. https://www.kaggle.com/code/syrahmadi/case-study-resale-hdb-flat-price-in-2012-2022
