# Matplot lib
## Draw a line
```python
%matplotlib inline
import numpy as np
from scipy.stats import norm
import matplotlib.pyplot as plt

x=np.arrange(-3,3,0.01)
plt.plot(x,norm.pdf(x))
```
### Multiple plot on one graph
```python
plt.plot(x,norm.pdf(x))
plt.plot(x,norm.pdf(x,1.0,0.5))
plt.show()
//save it to file
plt.savefig('C:\\venkata\\desktop\\Myplot.png',format='png')
```
### Adjust the axes
```python
axes = plt.axes()
axes.set_xlim([-5,5])
axes.set_ylim([0,1.0])
axes.set_xticks([-5,-4,-3,-2,-1,-0,1,2,3,4,5])
axes.set_yticks([0,0.2,0.4,0.6,0.8,1.0])
plt.plot(x, norm.pdf(x))
plt.plot(y, norm.pdf(x,1.0,0.5))
plt.show()
```
### Add a grid
```python
axes.grid()
```
### change line types and colors
```python
plt.plot(x,norm.pdf(x), 'b-') // b- = blue solid line
plt.plot(x,norm.pdf(x,1.0,0.5),'r:') // r: = red dotted
```
### Labeling and adding legend
```python
plt.xlabel('no of views')
plt.ylabel('date')
plt.legend(['no of views','date'],loc=4) //loc 4 refers to 4th quadrant
```
### XKCD style - like natural drawing
```python
plt.xkcd()
fig=plt.figure()
ax = fig.add_subplot(1, 1, 1)
ax.spines['right'].set_color('none')
ax.spines['top'].set_color('none')
plt.xticks([])
plt.yticks([])
ax.set_ylim([-30, 10])

data = np.ones(100)
data[70:] -= np.arange(30)

plt.annotate(
    'THE DAY I REALIZED\nI COULD COOK BACON\nWHENEVER I WANTED',
    xy=(70, 1), arrowprops=dict(arrowstyle='->'), xytext=(15, -10))

plt.plot(data)

plt.xlabel('time')
plt.ylabel('my overall health')
```
### Pie Chart
```python
\\remove XKCD mode
plt.rcdefaults()
values = [12,55,4,32,14]
colors = ['r','g','b','c','m']
explode = [0,0,0.2,0,0]
labels = ['India','United States','Russia','China','Europe']
plt.pie(values,colors=colors,labels=labels,explode=explode)
plt.title('Student Locations')
plt show()
```
### Bar Chart
```python
values = [12, 55, 4, 32, 14]
colors = ['r', 'g', 'b', 'c', 'm']
plt.bar(range(0,5), values, color= colors)
plt.show()
```
### Scatter plot
```python
from pylab import randn
#import matplotlib.pyplot as plt
X = randn(500)
Y = randn(500)
plt.scatter(X,Y)
plt.show()
```
### Histogram
```python
incomes = np.random.normal(27000, 15000, 10000)
plt.hist(incomes, 50)
plt.show()
```
### Box and Whisker
Useful for visualizing the spread & skew of data.
The red line represents the median of the data, and the box represents the bounds of the 1st and 3rd quartiles.
So, half of the data exists within the box.
The dotted-line "whiskers" indicate the range of the data - except for outliers, which are plotted outside the whiskers. Outliers are 1.5X or more the interquartile range.
This example below creates uniformly distributed random numbers between -40 and 60, plus a few outliers above 100 and below -100:
```python
uniformSkewed = np.random.rand(100) * 100 - 40
high_outliers = np.random.rand(10) * 50 + 100
low_outliers = np.random.rand(10) * -50 - 100
data = np.concatenate((uniformSkewed, high_outliers, low_outliers))
plt.boxplot(data)
plt.show()
```
