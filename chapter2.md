# Logistic Regression

Logistic regression is a classification method used when the response/observed variable $$Y$$ is categorical. Here we will only consider the case where $$Y$$ is a binary response variable, i.e. it takes value $$0$$ or $$1$$. The explanatory variable $$X$$ that help us predict $$Y$$ can be discrete or continuous. Our model is same linear model:
$$
\begin{aligned}
Y= \mu + \beta \cdot X
\end{aligned}
$$


How do we model the response such that our predictions are binary?

It turns out that we can do this using a logistic function. We model the $$P(Y=1|X,\beta)$$. This is given by:
$$
\begin{aligned}
P(Y=1|X,\beta) = g(\mu + \beta^TX)
\end{aligned}
$$
Here $$g(z)$$ is the logistic function:
$$
\begin{aligned}
g(z) = \frac{1}{1+exp(-z)}
\end{aligned}
$$
Using the logistic function, we can get the probability of $$Y$$ being $$0$$ or $$1$$.
$$
\begin{aligned}
P(Y=1|X,\beta) = \frac{1}{1+exp(\mu + \beta^TX)}
\end{aligned}
$$

Let's see how to do this using Python, R and MATLAB

*Please download example data from: https://raw.githubusercontent.com/princyparsana/cs438/master/data_files/binary.csv*

#### Python
```python
from sklearn import linear_model
import numpy as np

'''Read first line of the file - column names'''
col_names = []
with open('data_files/binary.csv','r') as fh:
        col_names.extend(fh.readline().strip().split(','))


fh.close()

'''Read the data file using genfromtxt function in NumPy. Skip reading the first line by skip_header, since we already have it in the list col_names'''
dat_ex = np.genfromtxt('data_files/binary.csv',delimiter=',',skip_header=1)

'''Dimensions od dat_ex'''
dat_ex.shape ## first entry it returns is number of rows and second is the number of columns.


'''The first column of this file is 'admit' which is a binary variable
where 0 represents that the student was not admitted to the
program and 1 represents students who were offered admission
So here first column is the response variable Y
We Use 300 samples for training and 100 for test'''
Y = dat_ex[0:300,0] # selecting all rows of column 0. In python indexing begins from 0
X = dat_ex[0:300,1::] # In this example we do not add constant ones, and hence specify fit_intercept=True in our model
model = linear_model.LogisticRegression(C=1e86) ''' Since scikit-learn implementation 
 of logistic regression is penalized version, 
 we set C - inverse of penalty parameter to a large number
 This leads to very low to no regularization'''
modelfit = model.fit(X,Y)
beta = modelfit.coef_
intercept = modelfit.intercept_
testX = dat_ex[300::,1::]
testY = dat_ex[300::,0]
'''
We use the fitted model to predict Y using our test data testX
'''
predicted_Y = modelfit.predict(testX)
```
####R
```R
#Read example dataset
dat.ex <- read.csv('data_files/binary.csv',header=T)

#Dimensions of dataset
dim(dat.ex)

# We use 300 samples for training
Y <- dat.ex[1:300,1]
X <- dat.ex[1:300,c(2,3,4)]
modelfit = glm(Y~1+.,family = binomial(),data = X) # 1 is for the intercept term and . represents all columns in X. Since our response variable Y is binary, family = binomial

#Test using 100 samples. In R, we can get response in the form of probability P(Y=1|X,beta)
testX <- dat.ex[301:400,c(2,3,4)]
testY <- dat.ex[301:400,1]
predict.prob<-predict(modelfit, newdata = testX, type = "response")
predicted.Y<-ifelse(predict.prob>0.5,1,0)
```

####MATLAB
```matlab
% Load data
dat_ex = dataset('File','data_files/binary.csv','Delimiter',',');
X = dat_ex(1:300,[2,3,4]);
Y = dat_exp(1:300,1);
testX = dat_ex(301:400,[2,3,4]);
testY = dat_exp(301:400,1);
modelfit = fitglm(double(X),double(Y),'Distribution','binomial')
predY_prob = predict(modelfit,double(testX));
predY=NaN(100,1);
predY(find(predY_prob =< 0.5)) = 0;
predY(find(predYprob > 0.5)) = 1;
```