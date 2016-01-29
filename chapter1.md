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

```python
from sklearn import datasets
from sklearn import linear_model

## Load iris dataset
iris = datasets.load_iris()


```