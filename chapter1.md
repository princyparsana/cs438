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

#### Python

```python
from sklearn import datasets
from sklearn import linear_model
import numpy as np
import matplotlib.pyplot as plt

## Load boston housing dataset
boston = datasets.load_boston()
X = boston.data
X = np.insert(X,0,1,axis=1) # constant for mean effect
Y = boston.target
''' Fit linear regression model'''
'''Since we have included the intercept term in X, 
if we do not include constant term for intercept in X,
then fit_intercept = True'''
model = linear_model.LinearRegression(fit_intercept=False) 
modelfit = model.fit(X,Y)
beta = modelfit.coef_
```
Here the length of $$\beta$$ is equal to # explanatory variables (columns in  $$X$$) +1 (for the mean term, $$\mu$$)

#### R
```R
require(MASS)
data(Boston)
target = as.numeric(Boston$medv) # median house prices in Boston
X = Boston[,c(1:13)] # Features that can help predict house prices in Boston
Y = target
model = glm(Y~1+., data = X, family = gaussian(link = identity))
beta = model$coefficients #here the first entry in beta is the intercept/mean effect term
```

#### MATLAB
```matlab
% load car dataset
load carsmall
X = [Weight Horsepower Cylinders Model_Year]; %Features that can help to predict mileage of a car
Y = MPG; %target variable - mileage
modelfit = fitlm(X,Y); % automatically fits intercept
beta = modelfit.Coefficients;
```
As we see above, the scripts above do the same thing. It learns the effect of each feature in X on the response variable Y.

## Principal Component Analysis
