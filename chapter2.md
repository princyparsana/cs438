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
P(Y==0|X,\beta) = g(
\end{aligned}
$$