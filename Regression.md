# Linear Regression
``` python
%matplotlib inline
import numpy as np
from pylab import *
pagespeeds = np.random.normal(3.0,1.0,1000)
purchaseAmount = 100-(pageSpeeds + np.random.normal(0,0.1,1000))*3
scatter(pageSpeeds, purchaseAmount)
```
## using scipy
``` python
from scipy import stats
slope, intercept, r_value, p_value, std_err = stats.linregress(pageSpeeds, purchaseAmount)
```
R-squared value tells how good the curve has been fit
r_value ** 2

## Let's use the slope and intercept we got from the regression to plot predicted values vs. observed:
``` python
import matplotlib.pyplot as plt
def Predict(x):
  return slope*x+intercept
  
fitLine = predict(pageSpeeds)

plt.scatter(pageSpeeds, purchaseAmount)
plt.plot(pageSpeeds, fitLine, c='r')
plt.show()
```
# Polynomial Regression


# Multivariate Regression
