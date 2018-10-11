# Please feel free to add more machine learning feature engineering points.

> This is by no means exhaustive.
> I hope to update all feature engineering methods, including domain specific ones like satellite data, ocean data, latitude and longitutde data as I get to know them. :)

1. Recursive Feature Elimination

	Recrusively eliminate features and fit the model to know the accuracy. Lets us konw which feature are important and also giving how many inputs will give the best result.
	
2. Univariate Feature Selection

	Tells us which input features have the strongest relationship wiht the output variable
	
3. Specify GridSearchCV a list on which it can perform hyperparameter tuning.

4. Indicator variable to highlight key information or explicitly notify key information.
	For example, predicting alcohol preferences, if age is present as a feature, then age >= 21 is an indicator we give as it is legal after that age. 
	
5. See if you can combine two or more features by taking their sum or difference or quotient or product.

6. Bring in external data
	For example, if you have street address, city and state, you could convert it to its latitude and longtitude and then bring in median_income_within_2_miles as a feature. 
	
7. Use sklearn's make_pipeline() and preprocess.scaler() function to sale the training and testing set appropriately.

8. Delete one row (or one feature) and run a benchmark on all algorithms . If the Classification accuracy increases, then you don't need it.

9. Get all interesting information if a date is provided, like, is_month_end, is_month_start, is_quarter_end, is_quarter_start, is_year_start, is_weekday, is_weekend, week_of_year and so forth.
      
