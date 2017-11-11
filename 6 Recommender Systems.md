# Recommender Systems
Based on your past behaviour 
people who bought also bought

## 1 User based collaborative filtering
- Build Matrix of things each use bought rated viewed
- compute similarity scores between users
- Find users similar to you
- recommend stuff that they bought/viewed/rated that you haven't

### problems with user based
people are fickle - tastes changes
There are many people than things - counting ???
people do bad things


## 2 item based collaborative filtering
people who liked an item
people who disliked an item
From the movie perspective 

``` python
import pandas as pd;
r_cols = ['user_id','movie_id','rating']
ratings = pd.read_csv('c:/venkata/ratings.data', sep='\t', names =r_cols,usecols=range(3), encoding = 'ISO-8859-1')

m_cols=['movie_id','title']
movies = pd.read_csv('C:/venkata/movies.data', sep='|', names = m_cols, usecols=range(3), encoding='ISO-8859-1')

//mering no wboth data sets using our pandas merge function
ratings = pd.merge(movies,ratings)

ratings.head()
```
