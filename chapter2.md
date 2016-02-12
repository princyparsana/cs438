# Logistic Regression

Logistic regression is a classification method used when the response/observed variable $$Y$$ is categorical. Here we will only consider the case where $$Y$$ is a binary response variable, i.e. it takes value $$0$$ or $$1$$. The explanatory variable $$X$$ that help us predict $$Y$$ can be discrete or continuous. Our model is same linear model:
$$
\begin{aligned}
Y= \mu + \beta \cdot X
\end{aligned}
$$

How do we model the response such that our predictions are binary?

It turns out that we can do this using a logistic function. We model the $$P(Y==0|X,\beta)$$. This is given by:
$$
\begin{aligned}
P(Y==0|X,\beta) = g(\beta_0 + \beta^TX)
\end{aligned}
$$
Here $$g(z)$$ is the logistic function:
$$
\begin{aligned}
g(z) = \frac{1}{1+exp(-z)}
\end{aligned}
$$
Using the logistic function, we can get the probability of $$Y$$ being $$0$$ or $$1$$ by:
$$
\begin{aligned}
P(Y==0|X,\beta) = \frac{1}{1+exp(\beta_0 + \beta^TX)}
\end{aligned}
$$

Let's see how to do this using Python, R and MATLAB

*Please download example data from: https://raw.githubusercontent.com/princyparsana/cs438/master/data_files/binary.csv*

```python
import numpy as np
import pandas as pd

```