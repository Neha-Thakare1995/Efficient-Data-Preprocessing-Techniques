# Efficient-Data-Preprocessing-Techniques

This Project analysis and implementation cover several important aspects of preprocessing and modeling in a dataset with missing values and outliers. Here’s a detailed breakdown of what you’ve done, along with some suggestions for improvement:

## 1. Encoding:
 - <b>RoadTrafficDensity:</b> Used Ordinal Encoding due to its natural ordering (Low, Medium, High, Jam).
 - <b>TypeOfVehicle, TypeOfOrder:</b> Applied Label Encoding to handle the categorical variables, especially since their frequency clashes.
 - <b>City:</b> Used Frequency Encoding due to the absence of repetition in values.
WeatherConditions: Applied One-Hot Encoding as it does not have a large sample space.
## 2. Scaling:

You compared various scaling techniques to determine their impact on the dataset:

 - <b>MinMaxScaler:</b> Scales values to a [0,1] range, preserving distribution shape.
 - <b>MaxAbsScaler:</b> Similar to MinMaxScaler but for data with zero mean, scales features by their maximum absolute value.
 - <b>Z-score (Standard Scaler):</b> Standardizes features to have mean 0 and variance 1, which can affect distributions with outliers.
 - <b>RobustScaler:</b> Scales features using statistics that are robust to outliers (median and IQR), preserving distribution.
 - <b>QuantileTransformer:</b> Transforms features to follow a Gaussian distribution, effective for skewed data.
 - <b>Log Transformation:</b> Useful for reducing skewness but can skew data further if not applied correctly.
Your analysis indicates that <b>Quantile Transformer</b> is suitable for normalizing distributions close to a Gaussian distribution, while <b>Robust Scaler</b> performs well with outliers.

## 3. Handling Missing Data and Outliers:

 - <b>Missing Data:</b> For categorical 'WeatherConditions,' you used the mode; for numerical data like 'TimeTaken' and 'DeliveryPersonAge,' you used the mean.
 - <b>Outliers:</b> Replaced outliers using IQR for 'Distance' and 'TimeTaken.'

## 4. Model Evaluation:
You used Linear Regression and K-Nearest Neighbors (KNN) to predict missing values and evaluated their performance using RepeatedKFold cross-validation with RMSE as the metric.

## 5. Final Model Selection:
Based on performance metrics, you decided to use Robust Scaler and Linear Regression for imputing missing values in 'DeliveryPersonAge.' You also implemented the model to predict missing values and updated the dataset accordingly.

