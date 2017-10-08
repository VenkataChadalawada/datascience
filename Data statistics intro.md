# Types of data:
- Numerical
- categorical
- ordinal

## Numerical
Represents some sorts of quantitative measurements
### Discrete Data
integer based counts of some events
eg:- how many purchases did a customer made per year
### Continuous Data
Has an infinite number of positive values
eg:- How much time did it take for a customer to check out

## Categorial
Qualitative data that has no inherit mathematical meaning
eg-gender , race, political parties, etc..
you can assign numbers to those categories inorder to represent them more compactly

## Ordinal
A mixture of numberical and categorical 
example movie ratings 1 to 5 , 1 represents poor and 5 represents very good

Note: Taken from Frank Kane classes.

# Statistics
## Mean
Aka Average - sum/total

## Median
sort and middle value
* Median is less susceptible to outliers
eg:-Mean household income of america is 71,500$ where as Median is 51,200$
median better represents tht typcial American income

## Mode
Most common value in the data set
eg:- no of kids in the neighborhood in each house
0,2,3,2,1,2,2,1,0
2 in this case
* it only works with discrete numerical data

```python
import numpy as np
incomes = np.random.normal(27000,15000,10000)
np.mean(incomes)

%matplotlib inline
import matplotlib.pyplot as plt
plt.hist(incomes,50)
plt.show()

np.median(incomes)
incomes=np.append(incomes,[10000000000])

np.mean(incomes)
np.median(incomes)

ages=np.random.randint(18,high=90,size=500)
ages

from scipy import stats
stats.mode(ages)

```
## Standard Deviation & Variance
### Variance
Variance describes how spread out the data is
Avg of squared differences from the mean
example:
what is the variance of data set(1,4,5,4,8)
mean = 1+4+5+4+8/5 = 22/5 = 4.4
diff from the mean = (-3.4, -0.4, 0.6, -0.4, 3,4)
squared differences = (11.56,0.16,0.36,0.16,12.96)
Avg of squared diff = (11.56,0.16,0.36,0.16,12.96)/5 = 5.04
sample variance vs population variance -> in sample variance we divide with n-1 eg: (11.56,0.16,0.36,0.16,12.96)/4
### Standard deviation
it is the square root of variance
sqrt(5.04) = 2.24

```python
import numpy as np
incomes = np.random.normal(100,20,500)
incomes.std()
incomes.var()
```

### Probability Distribution Function
Gives you the probability of a data point falls within some given range of a given value

## Data Distribution
### 1 Uniform Distribution
```python
%matplotlib inline
import numpy as np
import matplotlib.pyplot as plt

values = np.random.uniform(-10.0,10.0,10000)
plt.hist(values,50)
plt.show()
```
### 2 Normal / Guassian Distribution PDF
```python
import numpy as np
from scipy.stats import norm
import matplotlib.pyplot as plt
x=np.arrange(-3,3,0.01)
plt.plot(x, norm.pdf(x))

mu=0.5
sigma=0.2
values = np.random.normal(mu,sigma,500)
plt.hist(values,50)
plt.show()
```
### 3 Exponential Probability Density Function PDF (Power Law)
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import expon

x=np.arrange(0,10,0.001)
//arrange(start,end,numofvalues)
plt.plot(x,expon.pdf(x))
```
### 4 Binomial Probability Mass Function PMF (discrete)
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import binom
x=np.arrange(0,10,0.01)
//shape parameters n and p - n is x axis and p is y axis
n=10
p=0.5
plt.plot(x, binom.pdf(x,n,p))
```

### 5 Poisson Probability Mass Function PMF (continuous)
Example: My website gets on average 500 visits per day. What's the odds of getting 550?
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import poisson
mu=500
x=np.arrange(400,600,0.5)
plt.plot(x,poission.pmf(x,mu))
```

## Percentiles
```python
import numpy as np
import matplotlib.pyplot as plt
vals = np.random.normal(50,10,1000)
np.percentile(vals, 50)
```
### Moments
Qualitative measures of the shape of a probability density function
#### first moment - Mean
#### second moment - Variance
#### third moment - Skew
- Positive skew - longer tail on right
- negative skew - longer tail on left
#### fourth moment - Kurtosis
how thick is the tail and how sharp is the peak compared to normal distribution
higher peaks have higher kurtosis
```python
import numpy as np
import scipy.stats as sp
import matlabplot.pyplot as plt
vals = np.random.normal(0,0.5,10000)
plt.hist(vals, 50)
np.mean(vals)
np.var(vals)
sp.skew(vals)
//negative means left viceversa
sp.kurtosis(vals)
```








