# IMDB_Rating_prediction
Predict movies' IMDB rating score with machine learning techniques
by Liuzhao 'Carlos' Tang

Code file:
1. Exploratory Data Analysis.ipynb
2. Extracting_IMDB_Data.ipynb
3. Data Preprocessing.ipynb
4. Model Selection.ipynb

data file:
1. IMDA_DATA.csv
2. dependent_var.csv
3. features.csv

other:
1. Machine Learning Project Report.pdf
2. README.md

## Introduction
the project is to predict the IMDA score of a movie based on its properties and social network data with machine learning techniques.
 
This project provided a sight of estimating movie quality for industry analysts and insights for film distributors.

## Task Definition
**Task:** The project is to predict a movie’s rating score on IMDB.com based on its properties and related social data

**Evaluation:** Models will be evaluated on MSE.

## Data and Variables
The raw data came from an online dataset. It had 5043 rows and 28 columns(15 numerical variables, 12 categorical variables, and 1 target variable).

The dependent variable is the rating score(imdb_score).

The independent variables have two parts: properties variables and social network variables. 
- Properties variables are attributes of a movie such as an office box performance, duration, budget, years, aspect_ratio, content rating, casts, and so on. 
- The social network variables are social network indicators related to a movie like Facebook like and the number of reviews

## Methodology
### Pre-processing
- Missing Value
1. update missing values by extracting data from IMDB database with  the cinemagoer package
2. fill missing values with ‘Other’ for categorical variable and with the mean of variable for numeric variables
- Outerliers
1. locate variables that contained outliers based on EDA
2. removed it and recheck the variable distribution: if they were a mild outlier, keet it, and if they were not mild, remove it
- Feature Engineering
1. for categorical variables, there were two encoding strategies: (1)If the number of unique variables is low(color), used one-hot encoding.(2)If the number of unique variables is high, used hashing encoding technique.
2. for columns “movie_title” and “plot_keywords”, create two new features: word_num(the number of words), and avg_length(the average length of words)
3. No transformation for numeric variables

### Model Design
- Models and Methods
1. lasso regression model
2. support vector machine(SVM) model
3. random forest model
4. extreme gradient boosting model
5. blending ensemble model
6. stacking ensemble model

- Dataset Split
1. train set : test set = 80% : 20%

- Model Selection Process
![image](https://user-images.githubusercontent.com/64500682/169754418-ae736757-b907-4ba4-9e7f-1444614fa9d7.png)

## Result
Blending Ensemble Model had the lowest MES(0.645)
```
Model	                              MSE
Lasso Regression	            0.911
SVM	                            1.292
Random Forest	                    0.722
XGB	                            0.769
Blending Ensemble Model	            0.644
Stacking Ensemble Model	            0.653
```

Top 5 important features are: 
1. the number of voted users
2. the movie duration
3. the movie budget
4. the released year of movie
5. the number of users for reviews.

```
Feature name            Importance
num_voted_users	        0.211623
duration	        0.126319
budget	                0.069417
title_year	        0.065868
num_user_for_reviews	0.060038
```
## Conclusion
1. The blending ensemble model has the best performance score. The finding suggests to select the model to deploy into production.
2. the number of voted users, duration, budget, released year, and the number of users for reviews have the highest importance. the effect of Social newwork data is less than the movie properties data

## Future Work
- Data
1. Choose high quality dataset
- Feature engineering
1. check numeric variables' distribution. If they don't follow normal distribution, implement some transformations like box-cox transformation before standardization.
2. try other encoding technique for high cardinality columns
- Model
1. try other models like Extra Randomized Trees(ERT) and Neural Networks.
2. try other ensemble methods like bagging and Boosting
3. implment grid search for the second layer model in stacking ensemble methods
- Evaluation
1. use multiple metric to evaluate model performance
