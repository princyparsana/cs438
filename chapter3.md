# Likelihood ratio tests using logistic regression

####Logistic Regression - recap
Logistic regression is a classification method used when the response/observed variable $$Y$$ is categorical. Here we will only consider the case where $$Y$$ is a binary response variable, i.e. it takes value $$0$$ or $$1$$. The explanatory variable $$X$$ that help us predict $$Y$$ can be discrete or continuous. Our model is same linear model:
$$
\begin{aligned}
Y= \mu + \beta \cdot X
\end{aligned}
$$

Let us consider a situation where Y is a column vector and X is a column vector. Each instance in Y has a corresponding entry in X.

The coefficient $$\beta$$ in a linear model represents how strong is the effect of X on Y. Let us say X is one SNP and Y is our phenotype. In this case our null hypothesis would be that SNP X has no effect on phenotype Y. We can represent this as:
$$
\begin{aligned}
Y= \mu
\end{aligned}
$$
Our alternate hypothesis will be that SNP X is associated with the phenotype. We can represent this as:
$$
\begin{aligned}
Y= \mu + \beta \cdot X
\end{aligned}
$$

Since our phenotype Y is discrete, i.e. either 0 or 1, this is a classification problem and we use logistic regression to solve this.

So, can we reject the null hypothesis? We use the likelihood ratio test to find this. There are multiple ways you can do this: permutation testing, Wald Test and chi-squared test. The likelihood ratio test statistic approximately follows chi-squared distribution.

To do this:
####Python

```python
Y = np.asarray([0, 0, 1, 0, 0, 0, 0, 0, 1, 0]) # phenotype
X = np.asarray([2, 1, 2, 2, 0, 0, 0, 0, 2, 2]) #SNP
logit = sm.Logit(Y,X)
res = logit.fit()
# get p-value from likelihood ratio test
res.llr_pvalue # refer results class of logit her: http://statsmodels.sourceforge.net/0.6.0/generated/statsmodels.discrete.discrete_model.LogitResults.html
```

```R

```