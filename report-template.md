# Report: Predict Bike Sharing Demand with AutoGluon Solution
#### NAME HERE
Anoud saud Alfaydi
## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?

When attempting to submit predictions, it was realized that the 'count' column, which represents the bike sharing demand, contained negative values. Since bike sharing demand cannot be negative, these values needed to be changed to zero. This ensures the predictions are logically sound for the problem.
### What was the top ranked model that performed?

The top-ranked model after initial training was 'WeightedEnsemble_L2'. This ensemble model achieved a Kaggle score of 1.79981.
## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?

The exploratory data analysis revealed several key insights and led to the creation of new features:

Timestamp Column: The 'datetime' column, initially an object type, was converted to datetime objects to enable time-based feature extraction.
Time-Based Features: New features were extracted from the 'datetime' column, including 'year', 'month', 'day', 'hour', and 'dayofweek'.
Categorical Features: 'season', 'weather', and 'holiday' columns were treated as categorical features, as their numerical representation might mislead the model into assuming ordinal relationships.
Interaction Features: The notebook explored creating interaction features, such as 'temp_humidity' (temperature * humidity) and 'temp_atemp' (temperature * feeling temperature). This was to capture more complex relationships within the data.
Lag Features: Lag features were generated for the 'count' variable (target variable), including count_lag_1, count_lag_2, and count_lag_3 (lagged values by 1, 2, and 3 hours respectively). These features help the model learn from past demand patterns.
Rolling Mean Features: Rolling mean features were also created for the 'count' variable, such as count_rolling_mean_24 (24-hour rolling mean) and count_rolling_mean_72 (72-hour rolling mean). These capture longer-term trends in demand.
### How much better did your model preform after adding additional features and why do you think that is?

After adding additional features, the model's performance significantly improved. The Kaggle score decreased from 1.79981 to 0.60928. This substantial improvement is likely due to several reasons:

Enriched Information: The newly created features, especially the time-based, lag, and rolling mean features, provided the model with more context and information about the underlying patterns and trends in bike demand.
Better Representation of Relationships: Interaction features might have helped capture non-linear relationships between existing features, leading to a more nuanced understanding of the data.
Addressing Temporal Dependencies: Lag and rolling mean features directly addressed the temporal nature of the dataset, allowing the model to leverage historical demand information, which is crucial for time-series prediction.
## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?

After hyperparameter tuning, the model's performance further improved. The Kaggle score decreased from 0.60928 to 0.51331. This shows that fine-tuning the model's hyperparameters can lead to noticeable gains in accuracy.
### If you were given more time with this dataset, where do you think you would spend more time?

If given more time with this dataset, additional efforts could be focused on:

More Extensive Feature Engineering: Exploring more complex interaction terms, polynomial features, or external data sources (e.g., local events, holidays not already included, specific weather events) could provide more predictive power.
Advanced Time Series Modeling: While AutoGluon handles time series implicitly, investigating more specialized time series models or ensemble methods specifically designed for sequential data might yield better results.
Deep Learning Models: For highly complex patterns, experimenting with deep learning architectures, such as Recurrent Neural Networks (RNNs) or Transformers, could potentially capture intricate temporal dependencies.
Hyperparameter Optimization: Running more extensive hyperparameter searches, perhaps using more sophisticated search strategies like Bayesian optimization, could further fine-tune the models.
### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.
|model|hpo1|hpo2|hpo3|score|
|--|--|--|--|--|
|initial|-|-|-|1.79981|
|add_features|-|-|-|0.60928|
|hpo|0.0005|relu|0.1|0.51331|

### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.

![model_train_score.png](img/model_train_score.png)

### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

TODO: Replace the image below with your own.

![model_test_score.png](img/model_test_score.png)

## Summary

The project aimed to predict bike sharing demand using AutoGluon. The initial model achieved a Kaggle score of 1.79981. Significant improvements were observed after performing exploratory data analysis and adding new features, particularly time-based, lag, and rolling mean features, which reduced the score to 0.60928. Further refinement through hyperparameter tuning led to an even better score of 0.51331. The process highlighted the importance of data preprocessing, feature engineering, and hyperparameter optimization in achieving high-performing predictive models. Given more time, exploring more advanced feature engineering, specialized time series models, or deep learning approaches could potentially yield even greater accuracy.