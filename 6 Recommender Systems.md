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
movies = pd.read_csv('C:/venkata/movies.data', sep='|', names = m_cols, usecols=range(2), encoding='ISO-8859-1')

//mering no wboth data sets using our pandas merge function
ratings = pd.merge(movies,ratings)

ratings.head()

```
Now the amazing pivot_table function on a DataFrame will construct a user / movie rating matrix. Note how NaN indicates missing data - movies that specific users didn't rate.
``` python
movieratings = ratings.pivot_table(index=['user_id'], columns=['title'], values=['rating'])
movieratings.head()
```
let's extract series of users who rated Star wars

``` python
starwarsratings = movieratings['starwars(1977)']
starWarsRatings.head()
```
Pandas' corrwith function makes it really easy to compute the pairwise correlation of Star Wars' vector of user rating with every other movie! After that, we'll drop any results that have no data, and construct a new DataFrame of movies and their correlation score (similarity) to Star Wars:


``` python
similarMovies = movieRatings.corrwith(starWarsRatings)
similarMovies = similarMovies.dropna()
df = pd.DataFrame(similarMovies)
df.head(10)
```
(That warning is safe to ignore.) Let's sort the results by similarity score, and we should have the movies most similar to Star Wars! Except... we don't. These results make no sense at all! This is why it's important to know your data - clearly we missed something important.

``` python
similarMovies.sort_values(ascending=False)
```
Our results are probably getting messed up by movies that have only been viewed by a handful of people who also happened to like Star Wars. So we need to get rid of movies that were only watched by a few people that are producing spurious results. Let's construct a new DataFrame that counts up how many ratings exist for each movie, and also the average rating while we're at it - that could also come in handy later.

``` python
import numpy as np
movieStats = ratings.groupby('title').agg({'rating': [np.size, np.mean]})
movieStats.head()
# Let's get rid of any movies rated by fewer than 100 people, and check the top-rated ones that are left:
popularMovies = movieStats['rating']['size'] >= 100
movieStats[popularMovies].sort_values([('rating', 'mean')], ascending=False)[:15]

```
100 might still be too low, but these results look pretty good as far as "well rated movies that people have heard of." Let's join this data with our original set of similar movies to Star Wars:

``` python
df = movieStats[popularMovies].join(pd.DataFrame(similarMovies, columns=['similarity']))
df.head()
# And, sort these new results by similarity score. That's more like it!
df.sort_values(['similarity'], ascending=False)[:15]
```
Ideally we'd also filter out the movie we started from - of course Star Wars is 100% similar to itself. But otherwise these results aren't bad.
