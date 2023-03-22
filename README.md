# MLB-2024-FA-Salary-Prediction
Collection of linear regression and random forest models predicting MLB's 2024 top 15 free agent salary prediction
# Project Overview
* Created a tool that estimates free agent contract salaries to help players or agents negoiate their salaries during off-season.
* Made an API call to fangraphs website and scraped past 4 years worth of free agent contracts using python and postman. 
* Engineered features of categories of positions and ages.
* Optimized Linear, Lasso, and Random Forest Regressors using GridsearchCV to reach the best model. 
# Code & Resources Used
Python Version: 3.9.12
* Packages: pandas, numpy, sklearn, matplotlib, seaborn, json, requests, statsmodels.api
* Fangraph website: https://www.fangraphs.com/roster-resource/free-agent-tracker?pos=
* API call: https://www.youtube.com/watch?v=SEQjNEawceo
* Image insertion: https://github.com/ericrdrew/WBB-Analytics/blob/main/NCSU-SQ-Plot.ipynb
# API Call & Web Scrapping
Inspected the network of fangraphs.com to call for API and used Postman to test and recieve code to request data. Through the process we got 2020, 2021, 2022, 2023 season free agent contracts and got the following: 
* Name
* Position
* Age
* WAR
* Hitting side
* Throwing side
* Contract year
* Contract salary
* Annual salary
* Previous team
* Moved team 
# Data Cleaning
After scrapping the data, I got rid of the columns that are not useful for the prediction. I made the following changes:
* concatenated all four year worth of contract data
* Only left five columns which are: Name, WAR, age, position, Year Salary
* Dropped rows with any NA values
* Dropped rows with empty values in Year Salary column
* Made a column with position categories which are: INF, OF, P, DH, C, MULTI
* Made dummy variables for position category column to be modeled ready
* Created a data frame without the position category dummy variable to explore data and analyze
# EDA
I looked at summary statistics by age and position for salary as well as relationship between WAR and salary. Below are the few highlights from the findings

* <img width="434" alt="Screen Shot 2023-02-03 at 2 40 52 PM" src="https://user-images.githubusercontent.com/118776460/216706840-3de404fc-0a45-4cb6-9f14-b7eba25f3dca.png">
* <img width="433" alt="Screen Shot 2023-02-03 at 2 41 23 PM" src="https://user-images.githubusercontent.com/118776460/216706879-c99269ea-a324-4ee9-a735-876d8310b151.png">
* <img width="436" alt="Screen Shot 2023-02-03 at 2 41 30 PM" src="https://user-images.githubusercontent.com/118776460/216706988-7d90d542-c81c-47dc-8aa5-9cce100f8616.png">
# Model Building
First, I transformed the categorical variable into dummy variables, I also split the data into train and test sets with a test size of 20%. 

I tried the different models and evaluated them using Mean Absolute Error. I chose MAE because it is relatively easy to interpret and did not want it to be sensitive to outliers. 

Models: 
* Dummy regressor with medain value - Baseline for the model 
* Multiple Linear Regression - Also a baseline for the model
* Lasso Regression - Normalized regression for the sparse of categorical variable
* Random Fores - Also because of the sparsity associated with the data 

<img width="1018" alt="2024-Prediction" src="https://user-images.githubusercontent.com/118776460/227012713-088621b7-7686-4ffe-955a-9fb3f6d82ce1.png">


# Model Performance
Muliple LInear Regression and Lasso Regression had the exact same MAE values.

* Dummy regressor with medain value - 4029179.45
* Multiple Linear Regression - 3674192.5
* Lasso Regression - 3674192.5
* Random Fores - 3700749.8
