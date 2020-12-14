## 1.1 Linear Regression

#### 1.1.1 Ordinary Least Squares
* Fits a linear model to minimize the residual sum of squares between the observed targets in the dataset, and the targets predicted by the linear approximation.
* *class* sklearn.linear_model.**LinearRegression**
* *Useful Parameters:*
  * n_jobs - Number of jobs to use for the computation. Provides speedup for n_targets > 1 and sufficiently large problems.
* Coefficient estimates for Ordinary Least Squares rely on the independence of the features. 
  * i.e. Bad when features are correlated and columns of design matrix X have an approximate linear depedence (multicollinearity).
  * Would cause least-squares estimate to become highly sensitive to randome errors in the observed target, producing large variance.

#### 1.1.11 Logistic Regression
* Linear model for classification rather than regression.
* Othernames: logit regression, maximum-entropy classification (MaxEnt), log-linear classifier.
* Regularization is applied by default.
* Can handle dense and sparse input.
* *class* sklearn.linear_model.**LogisticRegression**
* *Useful Parameters:*
  * penalty - Specify the norm used in the penalization ({'I1', 'I2', 'elasticnet', 'none' (no regularization for 'none')}, default='I2')
  * dual - Boolean specifying dual or primal formulation. Prefer dual=False when n_samples > n_features.
  * random_state - Set an int to make shuffling of data the same.
  * solver - Algorithm to use in optimization problem ({'newton-cg', 'lbfgs', 'liblinear', 'sag', 'saga'}, default='lbfgs')
  * n_jobs

#### 1.1.12 Generalized Linear Regression (GLM) - i.e. TweedieRegressor
* Implements a generalized linear mode for the Tweedie distribution, which allows to model any of the following distributions using the appropriate 'power' parameter.
  * Normal
  * Poisson - Use if target values y are counts (non-negative integers) or relative frequencies (non-negative).
  * Gamma - If target values are positive and skewed.
  * Inverse Gaussian - If target values seem heavier tailed.
* Example uses -
  * Agriculture/weather modelling (number of rain events per year (Poisson), amount of rainfall per event (Gamma), total rainfall per year (Compound Poisson Gamma)).
  * Risk modeling/insurance policy pricing (number of claim events/policyholder per year (Poisson), cost per event (Gamma), total cost per policyholder per year (Compount Poisson Gamma)).
  * Predictive maintenance (number of production interruption events per year (Poisson), duration of interruption (Gamma), total interruption time per year (Compound Poisson Gamma)).
* *class* sklearn.linear_model.**TweedieRegressor**
* *Useful Parameters:*
  * power - Determines the underlying target distribution ({0 (Normal), 1 (Poisson}, (1,2) (Compound Poisson Gamma), 2 (Gamma), 3 (Inverse Gaussian)}, default=0)
  * alpha - Determines the regularization strength (default=1).
  

## 1.4 Support Vector Machines
* Supervised learning methods used for classification, regression, and outliers detection.
* Advantages:
  * Effective in high dimensional spaces.
  * Still effective when number of dimensions is greater than the number of samples.
  * Uses a subset of training points for decision function so it is memory efficient.
* Disadvantages:
  * If number of features is much greater than number of samples, must avoid overfitting in choosing Kernel functions and regularization term.
  * Do not directly provide probability estimates.
  
#### 1.4.1 Classification (SVC)
* SVC:
  * *class* sklearn.svm.SVC
  * C-support vector classification. May be impractical beyond tens of thousands of samples.
  * For larger datasets consider using sklearn.svm.LinearSVC or sklearn.linear_model.SGDClassifier instead, possibly after a sklearn.kernel_approximation.Nystroem transformer.
  * *Useful Parameters*:
    * kernel - Specifies kernel type to be used ({'linear', 'poly', 'rbf', 'sigmoid', 'precomputed'}, default='rbf')
    * random_state
* NuSVC:
  * *class* sklearn.svm.NuSVC
  * Nu-support vector classification. Similar to SVC but uses a parameter to control the number of support vectors.
  * *Useful Parameters*:
    * nu - Upper bound on the fraction of margin errors, and a lower bound of the fraction of support vectors. In the interval (0, 1] (default=0.5).
    * kernel - Specifies kernel type (SVC).
    * random_state
* LinearSVC:
  * *class* sklearn.svm.LinearSVC
  * Similar to SVC with parameter kernel='linear', but implemented in terms of liblinear rather than libsvm, so it has more flexibility in the choice of penalties and loss functions and should scale better to large numbers of samples.
  * *Useful Parameters*:
    * penalty - Specifies norm used in penalization ({'I1', 'I2'}, default='I2')
    * dual - Set dual=False when n_samples > n_features.
    * random_state - When dual=False, random_state has no effect on the results. Otherwise set an int for reproducible output.

#### 1.4.2 Regression (SVR)
* SVR:
  * *class* sklearn.svm.SVR
* NuSVR:
  * *class* sklearn.svm.NuSVR
* LinearSVR:
  * *class* sklearn.svm.LinearSVR
  * Scales better to larger numbers of samples.
