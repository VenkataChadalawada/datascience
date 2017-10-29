# Bayes' Theorem

#### P(A|B) = {P(A) P(B|A)} /  P(B)

#### Eg: P(Spam/Free) = {P(Spam) P(Free|Spam)} / P(Free)

Assuming the presence of different entities are independent of each other - "Naive" Bayes Theorem

Scikit Learn will help 
#### Step1
We need to first create a database using DataFrame from Pandas
``` python
from pandas import DataFrame
data = DataFrame({'message': [], 'class': []})
```
#### step2
 Feed with spam and Ham files directoreis
 ``` python
 
data = data.append(dataFrameFromDirectory('e:/venchad/DataScience/emails/spam', 'spam'))
data = data.append(dataFrameFromDirectory('e:/venchad/DataScience/emails/ham', 'ham'))
 ```
 
 ### full code
 ``` python
 import os
import io
import numpy
from pandas import DataFrame
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.naive_bayes import MultinomialNB

def readFiles(path):
    for root, dirnames, filenames in os.walk(path):
        for filename in filenames:
            path = os.path.join(root, filename)

            inBody = False
            lines = []
            f = io.open(path, 'r', encoding='latin1')
            for line in f:
                if inBody:
                    lines.append(line)
                elif line == '\n':
                    inBody = True
            f.close()
            message = '\n'.join(lines)
            yield path, message


def dataFrameFromDirectory(path, classification):
    rows = []
    index = []
    for filename, message in readFiles(path):
        rows.append({'message': message, 'class': classification})
        index.append(filename)

    return DataFrame(rows, index=index)

data = DataFrame({'message': [], 'class': []})

data = data.append(dataFrameFromDirectory('e:/venchad/DataScience/emails/spam', 'spam'))
data = data.append(dataFrameFromDirectory('e:/venchad/DataScience/emails/ham', 'ham'))
 ```
