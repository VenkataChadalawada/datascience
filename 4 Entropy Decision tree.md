# Entropy & Decision Trees

## Entropy: 
A measure of data set's disorder.
entropy of 0 - all the classes in data would be same
entropy is very high if it lot of classes.
##### computing entropy:
``` python H(S) = -P1lnP1-P2lnP2-......PnlnPn ```
Pi = proportion of that data for ith class


## Decision Trees
flow chart to help you decide for classification
Another form of SUPERVISED Learning

### How does the decision tree works:
At each step find the attribute we can use to partition the data to minimize the entropy of the data at next step
Also called as ID3
Greedy Algorithm - as it goes down the tree - it picks the decision that minimizes the entropy the most at that stage
note - this might not optimal tree . But it works great for data we trained on

## Random forests -
  we cut the data into random samples
  Eacg sample constructs the tree
  each resulting tree can vote on the right result
  
  Randomly re-sample the data input for each tree is called  Bootstrap Aggregating or Bagging
  
### EXAMPLE
``` python
import numpy as np
import pandas as pd
from sklearn import tree

input_file = "c:/venky/datascience/PastHires.csv"
df = pd.read_csv(input_file, header = 0)
df.head()
```
scikit-learn needs everything to be numerical for decision trees to work. So, we'll map Y,N to 1,0 and levels of education to some scale of 0-2. In the real world, you'd need to think about how to deal with unexpected or missing data! By using map(), we know we'll get NaN for unexpected values.
```python
d = {'Y': 1, 'N': 0}
df['Hired'] = df['Hired'].map(d)
df['Employed?'] = df['Employed?'].map(d)
df['Top-tier school'] = df['Top-tier school'].map(d)
df['Interned'] = df['Interned'].map(d)
d = {'BS': 0, 'MS': 1, 'PhD': 2}
df['Level of Education'] = df['Level of Education'].map(d)
df.head()
```
Next we need to separate the features from the target column that we're trying to bulid a decision tree for.
``` python
features = list(df.columns[:6])
features
```
Now actually construct the decision tree:
``` python
y = df["Hired"]
X = df[features]
clf = tree.DecisionTreeClassifier()
clf = clf.fit(X,y)
```
... and display it. Note you need to have pydotplus installed for this to work. (!pip install pydotplus)
To read this decision tree, each condition branches left for "true" and right for "false". When you end up at a value, the value array represents how many samples exist in each target value. So value = [0. 5.] mean there are 0 "no hires" and 5 "hires" by the tim we get to that point. value = [3. 0.] means 3 no-hires and 0 hires.
```python
from IPython.display import Image  
from sklearn.externals.six import StringIO  
import pydotplus

dot_data = StringIO()  
tree.export_graphviz(clf, out_file=dot_data,  
                         feature_names=features)  
graph = pydotplus.graph_from_dot_data(dot_data.getvalue())  
Image(graph.create_png())  
```
## Ensemble Learning
We'll use a random forest of 10 decision trees to predict employment of specific candidate profiles:
``` python
from sklearn.ensemble import RandomForestClassifier

clf = RandomForestClassifier(n_estimators=10)
clf = clf.fit(X, y)

#Predict employment of an employed 10-year veteran
print (clf.predict([[10, 1, 4, 0, 0, 0]]))
#...and an unemployed 10-year veteran
print (clf.predict([[10, 0, 4, 0, 0, 0]]))
```



