# Scikit-Learn Intro

#### Requirements for working with data in sklearn:
1. Features (X) and response (y) are separate objects.
2. Features and response should be numeric (no Strings, etc).
3. Features and reponse should  be numpy arrays.
4. Features and response should have specific shapes.

#### Training a machine learning model:
1. Import the class(es) you plan to use.
  * E.g. 
    ```python
    from sklearn.neighbours import KNeighborsClassifier
    ```
2. Store feature data in to 'X' and store response data in 'y'.
3. Split the data into train dataset and test dataset.
  * E.g.
    ```python
    from sklearn.model_selection import train_test_split
    ...
    X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=0, test_size=0.2)
    ```
  * Set random state seed to a number (e.g. 0) as best practice (will keep the model predictions the same no matter how it is run).
4. Instantiate the estimator.
  * "Estimator" is scikit-learn's term for model.
  * "Instantiate" means "make an instance of".
  * E.g.
    ```python
    knn = KNeighborsClassifier(n_neighbors=1)
    ```
  * Name of the object does not matter.
  * Can specify tuning parameters (i.e. "hyperparameters") during this step.
5. Fit the model with training data.
  * Model is learning the relationship between X and y (train data).
  * Occurs in-place.
  * E.g.
    ```python
    knn.fit(X_train, y_train)
    ```
6. Predict the response for a new observation.
  * New observations are called "out-of-sample" data.
  * Uses the information it learned during the model training process.
  * Can pass in one datapoint, one dataset (e.g. X_test), or an array of datapoints.
  * E.g.
    ```python
    knn.predict([3, 4, 5, 2])
    ```
  * 'predict' returns a Numpy array.
