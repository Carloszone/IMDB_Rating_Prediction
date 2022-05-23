# IMDB_Rating_prediction
Predict movies' IMDB rating score with machine learning techniques
by Liuzhao 'Carlos' Tang

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
Lasso Regression	            0.912
SVM	                            1.707
Random Forest	                    0.728
XGB	                            0.769
Blending Ensemble Model	            0.645
Stacking Ensemble Model	            0.665
```
## Conclusion
1. The blending ensemble model has the best performance score. The finding suggests to select the model to deploy into production.

## Future Work
- Data. Choose high quality dataset
- Feature engineering
1. check numeric variables' distribution. If they don't follow normal distribution, implement some transformations like box-cox transformation before standardization.
2. try other encoding technique for high cardinality columns
- Model
1. try other models like Extra Randomized Trees(ERT) and Neural Networks.
2. try other ensemble methods like bagging and Boosting
3. implment grid search for the second layer model in stacking ensemble methods
- Evaluation
- use multiple metric to evaluate model performance
