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
### What if your data doesn't look linear at all? Let's look at some more realistic-looking page speed / purchase data:
example:
``` python
%matplotlib inline
from pylab import *
import numpy as np

np.random.seed(2)
pageSpeeds = np.random.normal(3.0, 1.0, 1000)
purchaseAmount = np.random.normal(50.0, 10.0, 1000) / pageSpeeds

scatter(pageSpeeds, purchaseAmount)
```
### numpy has a handy polyfit function we can use, to let us construct an nth-degree polynomial model of our data that minimizes squared error. Let's try it with a 4th degree polynomial:
``` python
x = np.array(pageSpeeds)
y = np.array(purchaseAmount)

p4 = np.poly1d(np.polyfit(x, y, 4))
```
### We'll visualize our original scatter plot, together with a plot of our predicted values using the polynomial for page speed times ranging from 0-7 seconds:
``` python
import matplotlib.pyplot as plt

xp = np.linspace(0, 7, 100)
plt.scatter(x, y)
plt.plot(xp, p4(xp), c='r')
plt.show()
```
#### Looks pretty good! Let's measure the r-squared error:
``` python
from sklearn.metrics import r2_score

r2 = r2_score(y, p4(x))

print(r2)
```
o/p 0.8293766

# Multivariate Regression

# MultiLevel Models
the concept is  - some effects happens in various levels
