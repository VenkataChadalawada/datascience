# Ensemble Learning
Bunch of decision trees using different sub samples of data - They all vote at the end
different K-means models voting different centroids - They all vote at the end
more than 1 model it might be same or diff - they all can vote.

Random Forests uses technique called Bagging - 
#### Boosting -
    Its an alternate technique where Each subsequent model in the ensemble boosts attributes that address data misclassified in the 
    previous model
#### Bucket of models - eg: K-means, Decission tree & regression
    Trains several different models using training data and picks the one that works best with the test data
Stacking- Runs multiple models and once on the data and combines the results.

Bayesian parameter averaging  ~~~same results as~ Bagging
bayesian model Combination ~~~~ruled out by~~ cross validation
