IMDb Score Prediction for 2024 Winter Movies

This project involves analyzing a movie dataset to predict IMDb scores for 10 upcoming winter 2024 movies using a regression model with splines and transformations.


Project Overview

The objective of this project is to predict IMDb scores for 10 upcoming movies based on features such as budget, duration, director rating, genre, and other movie characteristics. It uses a generalized linear model (GLM) with spline transformations to capture non-linear relationships effectively.


Features

	1.	Data Visualization:
	•	Boxplots, histograms, scatter plots with trend lines, and spline visualizations for features such as IMDb scores, duration, and budgets.
	2.	Data Transformation:
	•	Log transformations for variables with skewed distributions (e.g., movie_meter_IMDBpro).
	•	Binary encoding for categorical variables like language and color_film.
	3.	Predictive Model:
	•	Generalized linear model with spline transformations for non-linear relationships.
	•	Cross-validation to optimize the model and minimize mean squared error (MSE).
	4.	Prediction:
	•	IMDb scores for 10 upcoming movies using the trained model.


 Data Processing

	1.	Log Transformations:
	•	Variables like movie_meter_IMDBpro, actor1_star_meter, actor2_star_meter, and actor3_star_meter were log-transformed to handle skewness.
	2.	Binary Encoding:
	•	Encoded variables such as language, country, and color_film.
	3.	Feature Engineering:
	•	Computed the average IMDb score for each director and merged it into the dataset.
	•	Counted the number of genres for each movie.
	•	Scaled continuous variables for uniformity.
	4.	Outlier Removal:
	•	Identified and removed outliers using residual plots and tests.
	5.	Collinearity Check:
	•	Calculated Variance Inflation Factors (VIF) to identify multicollinearity and adjusted the predictors accordingly.


 odel Building and Validation

	1.	Model Selection:
	•	Used splines for non-linear predictors such as movie_budget, duration, avg_director_score, and release_year.
	•	Optimized spline knots and degrees via cross-validation (20-fold).
	2.	Polynomial Regression:
	•	Evaluated different polynomial degrees for predictors and selected optimal degrees via ANOVA.

 fit = glm(imdb_score ~ 
            bs(avg_director_score, knots = c(quantile(avg_director_score, 0.1), quantile(avg_director_score, 0.99)), degree = 2) +
            bs(movie_meter_IMDBpro, knots = c(quantile(movie_meter_IMDBpro, 0.01), quantile(movie_meter_IMDBpro, 0.95)), degree = 1) +
            bs(duration, knots = c(quantile(duration, 0.05), quantile(duration, 0.85)), degree = 3) +
            bs(movie_budget, knots = c(quantile(movie_budget, 0.5), quantile(movie_budget, 0.65)), degree = 1) +
            drama + horror + movies_english, data = movies)

            Predictions

	•	Dataset: 10 upcoming winter 2024 movies (test_data_IMDB_Fall_2024.csv).
	•	Steps:
	1.	Preprocessed the test data similarly to the training data.
	2.	Predicted IMDb scores using the trained model.
	•	Output:
Predicted IMDb scores ranged between 6.5 and 8.2 (example).


Future Improvements

	1.	Feature Expansion:
	•	Include additional predictors like social media trends, user reviews, or actor popularity.
	2.	Model Enhancement:
	•	Explore machine learning models like Random Forest or Gradient Boosting for improved predictions.
	3.	Deployment:
	•	Create a web application for real-time IMDb score predictions.
	4.	Sensitivity Analysis:
	•	Study the sensitivity of predictions to individual features.
