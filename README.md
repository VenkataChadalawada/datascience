# datascience

##Pandas
```python
import pandas as pd
df=pd.read_csv('Employees')
//top 5 records
df.head()
//top n records
df.head(n)
//last 5 records
df.tail()
//last n records
df.tail(n)
//(columns,rows)
df.shape
//total size of the data frame cols*rows
df.size
//num of rows
len(df)
//list all columns
df.columns
//extract single column
df['Hired']
//you can also extract given range of rows from the coulmn
df['Hired'][:5]
//or even single value in that row
df['Hired'][5]
//extract more than one column
df[['Experience']['Hired']]
//extract specific ranges of rows in those columns
df[['Experience']['Hired']][:5]
//sorting the data frame with specific column
df.sort_values(['Experience'])
//you can break down unique values in a given columns into rows
degree_counts = df['EducationLevel'].value_counts()
//pandas even make it into a histogram of those counts by simply calling plot
degree_counts.plot(kind='bar')

Exercise
Try extracting rows 5-10 of our DataFrame, preserving only the "Previous Employers" and "Hired" columns. Assign that to a new DataFrame, and create a histogram plotting the distribution of the previous employers in this subset of the data.
import pandas as pd
df=pd.read_csv('PastHires.csv')
rows5to10 = df[5:11]
only2=rows5to10[['Previous employers', 'Hired']]
print only2
only2['Previous employers'].plot(kind='bar')
```

