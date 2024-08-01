# Movie Recommendation Engine

This project aims to recommend movies to users based on their preferences using collaborative filtering.

## Datasets

The main dataset is "Netflix_Data", formed by combining the "Netflix_Dataset_Rating" and "Netflix_Dataset_Movie2" datasets.

- **Netflix_Dataset_Rating**: Includes `User_ID`, `Rating`, and `Movie_ID` columns.
- **Netflix_Dataset_Movie2**: Includes `Movie_ID`, `Year`, and `Name` columns.

Both datasets are merged on the `Movie_ID` column.

## Libraries Used

- Pandas
- PySpark
- Matplotlib
- Numpy
- Seaborn

## Data Preparation

The dataset is divided into two parts: 70% for training and 30% for testing.

```python
training_data, test_data = df.randomSplit([0.7, 0.3], seed=5064)
```
Model Training
We used ALS (Alternating Least Squares) for training the recommendation model, with the last 4 digits of my student number as the seed. The parameters of ALS were adjusted and the algorithm was re-run with different values for rank (10, 50, 200), iteration (10, 50, 200), and lambda (0.01, 0.1). This resulted in 18 different models being created using the specified rank-iteration-lambda combinations.

Parameters Explanation
Rank: Determines the number of columns in the output matrix, controlling the dimension of the factor matrices.
Iteration: The number of times the optimization loop of the ALS algorithm will run. Each iteration updates the factor matrices to reduce the error.
Lambda: A regularization parameter to control overfitting, governing the amount of regularization applied to the model.
Model Evaluation
The MSE and RMSE results of each model were extracted. The model with the lowest RMSE was chosen as the best.

MSE (Mean Squared Error): Measures the average squared difference between predicted and true values.
RMSE (Root Mean Squared Error): The square root of MSE, providing a metric in the same scale as the original target variable.
The best model is the one with the lowest MSE and RMSE values.

Results
Best Parameter Combination
RMSE: 1.2946339724178337
Rank: 50
MaxIter: 20
RegParam: 0.1
Comparison of Predictions with Actual Values


Cosine Similarity Method
Using the Cosine Similarity method, the 10 most similar users were found based on the movie with Movie_ID 148.

Movie_ID: 148
Similar Users:
(51690, 0.9999999999999998)
(1417990, 0.9999999999999998)
(1553750, 0.9999999999999998)
(508111, 0.9999999999999998)
(748251, 0.9999999999999998)
(1919701, 0.9999999999999998)
(2191211, 0.9999999999999998)
(2253871, 0.9999999999999998)
(2287271, 0.9999999999999998)
(732492, 0.9999999999999998)
Recommended Movies for a Specific User
Finally, 10 movies that the user with the entered User_ID might like are listed.

User_ID: 2031561
Recommended Movies:
Movie ID: 253, Rating: 3.812014102935791
Movie ID: 197, Rating: 3.7051990032196045
Movie ID: 165, Rating: 3.5358362197875977
Movie ID: 270, Rating: 3.487565517425537
Movie ID: 359, Rating: 3.4370224475860596
Movie ID: 191, Rating: 3.424190044403076
Movie ID: 241, Rating: 3.4208264350891113
Movie ID: 76, Rating: 3.410930871963501
Movie ID: 152, Rating: 3.396789073944092
Movie ID: 143, Rating: 3.3912668228149414
Summary
This project showcases the creation of a movie recommendation engine using collaborative filtering techniques with PySpark's ALS algorithm. The dataset, model training process, parameter tuning, and evaluation metrics are detailed. The best model was selected based on RMSE, and recommendations were made using cosine similarity.

For a detailed view of the dataset summary, visualizations, and code, please browse the provided Jupyter Notebook.

Contact
Feel free to reach out to me anytime for further questions or discussions!
