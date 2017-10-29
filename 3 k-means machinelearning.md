# K-Means Clustering
#### Attemplts to split data into K groups that are closest to K Centroids
unsupervised learning - uses only the positions of each data point
can uncover interesting behaviours
Where do Millioniares live?
What genres of music / movies etc naturally fall out of data?
create your own stereotypes from given demographics of data

#### choosing K  - Try increasing K values until u stop getting large reductions in squared error (distances from each point to their centroids)
note: no labelling - you cant tell the meaning - upto us to dig into data and describe that in english

### Activity:
#### Step 1 Lets create some mock data

```python 
from numpy import random, array
# Create fake income/age clusters for N people in k clusters
def createClusteredData(N, k):
    random.seed(10)
    pointsPerCluster = float(N)/k
    X = []
    for i in range (k):
        incomeCentroid = random.uniform(20000.0, 200000.0)
        ageCentroid = random.uniform(20.0, 70.0)
        for j in range(int(pointsPerCluster)):
            X.append([random.normal(incomeCentroid, 10000.0), random.normal(ageCentroid, 2.0)])
    X = array(X)
    return X
```
#### Step 2 We'll use k-means to rediscover these clusters in unsupervised learning:
``` python
%matplotlib inline

from sklearn.cluster import KMeans
import matplotlib.pyplot as plt
from sklearn.preprocessing import scale
from numpy import random, float
#create data object using our mock method above
data = createClusteredData(100, 5) 
#create a model object with k clusters
model = KMeans(n_clusters=5)
# Note I'm scaling the data to normalize it! Important for good results.
model = model.fit(scale(data))
# We can look at the clusters each data point was assigned to
print(model.labels_)

# And we'll visualize it:
plt.figure(figsize=(8, 6))
plt.scatter(data[:,0], data[:,1], c=model.labels_.astype(float))

```
o/p [0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
 1 1 1 4 4 4 4 4 4 4 4 4 4 4 4 4 4 4 4 4 4 4 2 3 3 3 3 3 3 3 3 3 3 3 3 3 3
 3 3 3 3 3 3 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2]

