# Predict Goodreads Book Rating
## Project Description
"Don't judge a book by its cover". Then can we judge the book based on a combination of cover, title, description, length, etc.? This project tries to answer that question by building a prediction model using an available dataset. The model solves a regression problem by predicting the average rating of a given book on Goodreads.  

There are 3 main tasks in this project:
- Data exploration: Explore at least 3 columns or column pairs using appropriately descriptive statistics and graphs.
- Feature engineering: Use suitable Python approaches to extract potential features for model input. Conduct appropriate analysis to evaluate feature importance, then use suitable methods to select the final features for training/testing model. 
- Modelling: Split the data appropriately and explore different machine learning algorithms to build a predictive model.

## Experiment Design
We split the data into train and validation sets by an 80/20 ratio. Next, we build 4 base models to predict the rating. Each model utilizes a subset of features and performs a distinct task as follows:
- Base model 1: Predict the average rating baed on the tf-idf matrices converted from the description column.
- Base model 2: Predict the average rating by analyzing the numeric features rating_count, review_count, number_of_pages and publication_year.
- Base model 3: Analyze the description column based on lexicon and predict the average rating. 
- Base model 4: Use sentiment analysis on the description column to predict the average rating.

For each base model, we try out 4 popular algorithms in machine learning which include XGBoost, random forest, Bayesian Ridge, and CatBoost. Finally, we linearly stack these models and build a meta model from one of the algorithms mentioned above. 

The evaluation metric is root mean square error (RMSE).

## Model Evaluation
| | Base model 1 | Base model 2 | Base model 3 | Base model 4 | Meta model | RMSE | MSE | r2 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Model 1 | XGBoost | XGBoost | XGBoost | Random forest | XGBoost | 0.2981 | 0.2259 | 0.3917 |
| Model 2 | Bayesian Ridge | XGBoost | CatBoost | Random forest | XGBoost | 0.3070 | 0.2310 | 0.3544 |
| Model 3 | XGBoost | Random forest | XGBoost | Random forest | XGBoost | 0.3144 | 0.2311 | 0.3230 |

After experimenting with multiple algorithms, we arrive at the final 3 best working models. Model 1, which uses XGBoost and random forest in its base and meta models, achieves the lowest RMSE score. 

## Conclusion
Upon completion of this project, we have successfully built 3 baseline models to predict the book rating on Goodreads. These models could be further improved in the future by exploring more advanced neural networks for the sentiment analysis task and performing an in-depth parameter tuning process. 

## Acknowledgements
The books are scraped from a list of titles called "Best Books Ever" which can be found at https://www.goodreads.com/list/show/1.Best_Books_Ever page.