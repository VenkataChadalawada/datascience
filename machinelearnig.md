What is Machine Learning?
Algorithms that can learn from observational data and can make predictions out of it

# Supervised vs Un Supervised
##### Basic difference in layman terms : In supervised learning, the output datasets are provided which are used to train the machine and get the desired outputs whereas in unsupervised learning no datasets are provided, instead the data is clustered into different classes .

# Train Test Method
``` python
%matplotlib inline
import numpy as np
from pylab import *
np.random.seed(2)

pagespeed = np.radom.normal(3.0,1.0,100)
purchaseAmount = np.random.normal(50.0,30.0,100)/pagespeed

scatter(pagespeed, purchaseAmount)
```
#### lets take 80% as train data and 20% as test data
``` python
trainX = pagespeed[:80]
testX = pagespeed[20:]

trainY = purchaseAmount[:80]
testY = purchaseAmount[20:]

scatter(trainX,trainY)
// then
scatter(testX, testY)
```

#### Now we'll try to fit an 8th-degree polynomial to this data (which is almost certainly overfitting, given what we know about how it was generated!)
``` python
x= np.array(trainX)
y=np.array(trainY)
p4=np.polyld(np.polyfit(x,y,8))
```

#### Let's plot our polynomial against the training data:
``` python
import matplotlib.pyplot as plt
xp = np.linspace(0,7,100)
axes = plt.axes()
axes.set_Xlim([0,7])
axes.set_Ylim(0,200])
plt.scatter(x,y)
plt.plot(xp,p4(xp),c='r')
plt.show()
```
#### Against our test data
``` python
xp = np.linspace(0, 7, 100)
testx=np.array(testX)
testy=np.array(testY)
axes = plt.axes()
axes.set_Xlim([0,7])
axes.set_Ylim([0,200])
plt.scatter(testx,testy) //points scattered
plt.plot(xp,p4(xp),c='r') //line plotted
plt.show()

```
#### Doesn't look that bad when you just eyeball it, but the r-squared score on the test data is kind of horrible! This tells us that our model isn't all that great...
``` python
from sk_learn.metrics import r2_score
r2 = r2_score(texty,p4(testx))
print r2
```

```python
from sk_learn.metrics import r2_score
r2 = r2_score(np.array(trainY),p4(np.array(trainX)))
print r2
```

