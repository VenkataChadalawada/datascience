# Covariance 
Measures how two variables vary in tandem from their means
SIGMA (Xmean - Xi) . (Ymean - Yi) / n-1

# Correlation
Just divide the covariance by the standard deviation of both variables and that normalize things.
so correlation of perfect -1 means a perfect Inverse correlation
0 - no correlation
1 - perfect correlation

Remember Correlation does not imply causation

only a controlled randomized experiment can give you insights on Causation

Use correlation to decide what experiements to conduct

eg:-

``` python
def de_mean(x):
  xmean = mean(x)
  return [xi - xmean for xi in x]
  
def covariance(x,y):
  n=len(x)
  return dot(de_mean(x),de_mean(y))/n-1
  
pageSpeeds = np.random.normal(3.0,1.0,1000)
purchaseAmount = np.random.normal(50.0,10.0,1000)

scatter(pageSpeeds, purchaseAmount)

covariance(pageSpeeds, purchaseAmount)
```
