# Basic ML with Python, R and MATLAB

We will be covering couple of basic machine learning methods and an example on how to use them with Python, R and MATLAB.
##  Linear Regression

Linear regression is one of the most basic and widely used machine learning method. A linear model consists of an explanatory variable X and response variable Y. It can be represented as:

$$
\begin{aligned}
Y= \mu + \beta \cdot X
\end{aligned}
$$

Here, $$\mu$$ is the mean effect and $$\beta$$ is the effect of the explanatory variable X on the response variable Y.

Let's see how this works


#### Python

```python
from sklearn import datasets
from sklearn import linear_model
import numpy as np
import matplotlib.pyplot as plt

## Load iris dataset
iris = datasets.load_iris()
X = iris.data
X = np.insert(X,0,1,axis=1) # constant for mean effect
Y = iris.target
model = linear_model.LinearRegression(fit_intercept=False) #Since we have included the intercept term in X
modelfit = model.fit(X,Y)
beta = modelfit.coef_
```
Here the length of $$\beta$$ is equal to # explanatory variables (columns in  $$X$$) +1 (for the mean term, $$\mu$$)

#### R
```R
data(iris)
iris = iris
target = as.numeric(iris$Species)
X = iris[,c(1,2,3,4)]
Y = target
model = lm(Y~ 1+ X$Sepal.Length+X$Sepal.Width+X$Petal.Length+X$Petal.Width)
beta = model$coefficients
```

#### MATLAB
```MATLAB

```