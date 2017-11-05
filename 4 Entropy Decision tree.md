# Entropy & Decision Trees

## Entropy: 
A measure of data set's disorder.
entropy of 0 - all the classes in data would be same
entropy is very high if it lot of classes.
##### computing entropy:
H(S) = -P1lnP1-P2lnP2-......PnlnPn
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
  
  Randomly re-sample the data input for each tree is called ##### Bootstrap Aggregating or Bagging
  
### EXAMPLE



