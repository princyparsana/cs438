# How to make Q-Q plots?

### What are Q-Q plots?
A q-q plot is a plot that is used to compare two distributions against each other. It helps you to identify if your assumptions of a distribution are valid. P-values under null hypothesis follow a uniform distribution. p-values can be obtained from tests such as t-test, f-test, rank-sum test, etc. The x-axis on q-q plot represents the theoretical p-values (uniformly distributed). The y-axis represents observed p-values, i.e. the ones we obtain from testing.

#### So how do we make these plots?

##### MATLAB
```Matlab
% number of tests
n = 5000
% creating dummy variable
obs_p = rand(n,1);
% sort observed p-values. Since these tests can give very small p-values, we transform by taking -log10(p-value)
obs_p = -log10(sort(obs_p));
% creating theoretical p-values that follow a uniform distribution
th_p = -log10(1/n:1/n:1);
scatter(th_p, obs_p)
hline = refline(1,0);
set(hline,'Color','r')
```
##### Python
```python
import numpy as np
import matplotlib.pyplot as plt
# number of tests
n = 5000
# creating dummy observed p-values
obs_p = np.random.rand(1,n)[0]
obs_p = -np.log10(np.sort(obs_p))
th_p = np.arange(1/float(n),1+(1/float(n)),1/float(n))
th_p = -np.log10(th_p)
fig, ax = plt.subplots(ncols=1)
ax.scatter(th_p,obs_p)
x = np.linspace(*ax.get_xlim())
ax.plot(x, x)
plt.show()
```
##### R
```R
# number of tests
n = 3000
# creating dummy observed p-values
obs_p = runif(n)
obs_p = -log10(sort(obs_p))
th_p = -log10(seq(1/n,1,1/n))
plot(th_p,obs_p)
lines(th_p,th_p,col='red')
```


