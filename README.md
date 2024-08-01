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


Used ALS (Alternating Least Squares) for training recommendation model with last 4 digit of my student number as a “seed”. Also changed the parameters of ALS re-run the algorithm for parameters “rank” (10, 50, 200), “iteration” (10, 50, 200) and “lambda” (0.01, 0.1). This means 18 different model will be created using specified rank-iteration-lambda values.

[ALS_67dc3018ec83, ALS_ec2f33f8c1b8, ALS_0b091e615f48, ALS_64d15ae1a5b0, ALS_7f5153eea5c5, ALS_b617f5cf9e55, ALS_63de1ef8b47d, ALS_5a345d2d2c8b, ALS_a550efaba091, ALS_93e42f00a434, ALS_8e7a12d081ed, ALS_dc1a4f3a6a08, ALS_1f11b082512d, ALS_34c4e695f431, ALS_8a6602f6ca42, ALS_225cffd95582, ALS_71492501a4e9, ALS_bff5c48f598b]

Rank: Rank is a fundamental parameter of the ALS algorithm that determines the number of columns in the output matrix. In other words, it controls the dimension of the factor matrices in the ALS model.
Iteration: Iteration is a parameter that determines the number of times the optimization loop of the ALS algorithm will run. In each iteration, the ALS model updates the factor matrices and aims to reduce the error. 
Lambda: Lambda is a regularization parameter in the ALS algorithm, used to control overfitting. The lambda value governs the amount of regularization applied to the model.

The MSE and RMSE results of each model were extracted and the model with the lowest RMSE was decided to be the best.
MSE is a metric used to measure the average squared difference between the predicted values and the true values in a regression problem.
RMSE is the square root of MSE, and it provides a metric that is in the same scale as the original target variable.
The MSE and RMSE values represent the error rate. The best model is the one with the lowest values of these metrics. Therefore, based on this criterion.
Results:
The best parameter combination:
RMSE: 1.2946339724178337
Rank: 50, MaxIter: 20, RegParam: 0.1

The predictions of the best model were compared with the actual values.
![image](https://github.com/user-attachments/assets/4389caac-f309-44d0-a4b3-e16c05f6c3e7)

Using the CosineSimilarity method, the 10 most similar users were found based on the movie with Movie_ID 148.
Movie_ID : 148
[(51690, 0.9999999999999998), (1417990, 0.9999999999999998), (1553750, 0.9999999999999998), (508111, 0.9999999999999998), (748251, 0.9999999999999998), (1919701, 0.9999999999999998), (2191211, 0.9999999999999998), (2253871, 0.9999999999999998), (2287271, 0.9999999999999998), (732492, 0.9999999999999998)]

Finally, 10 movies that the user with the entered User_ID might like are listed.
User_ID : 2031561

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

The last two operations are the exact opposite of each other.

You can browse the iPynb file to see and interpret the summary of the dataset, visualizations and examine the Codes in more detail :)
You can contact me anytime :=)
