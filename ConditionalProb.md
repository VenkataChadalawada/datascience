# Conditional Probability
P(B|A) Probability of B given A has occured
We know:
### P(B|A) = P(A,B) / P(A)
Probability of A and B both occuring

60% of students passed both tests
80% passed first one
prob of passing second test given first test
P(A,B)/P(A) = 0.6/0.8 = 0.75

ex:-
lets say we have different age group people and their purchases. Lets say age group increasing ->increases the purchases
P(E|F) where E is purchase and F is you are age grop 30
so probability of someone in 30's buying something

``` python
P(E/F) = float(purchases[30])/float(totals[30])
print "P(purchases|30s):",PEF
O/P 0.29992

//PF - prob of being 30 in the data set
PF = float(totals[30])/ 10000.0
o/p 0.16619

//PE -overall probability of buying somehting regardless of your age
PE = float(totalpurchases)/10000.0
o/p 0.45012

#### If E & F were independent then we would expect P(E/F) is about the same as P(E). But they aren't as P(E)=0.45 & P(E/F) = 0.3 
so E & F are dependent

P(E)P(F) = P(E) * P(F) = 0.0748

#### P(E,F) is different from P(E|F). P(E,F) would be the probability of both being in your 30's and buying something, out of the total population - not just the population of people in their 30's:

#### P(E,F) = P(E)P(F), and they are pretty close in this example. But because E and F are actually dependent on each other, and the randomness of the data we're working with, it's not quite the same.
We can also check that P(E|F) = P(E,F)/P(F) and sure enough, it is:

P(E,F) = P(30's,purchase) = float(purchases[30])/10000.0 /PF
0.04

```
# Bayes Theorem
### P(A/B) = (P(A) P(B/A)) /  P(B)

Example: 
Event A = Is the User of Drug
Event B = tested positive for the Drug
eg:
P(A/B) = P(A) P(B/A) / P(B) = 0.003 * 0.99 / 0.013 = 22.8%
so the odds of someone being an actual user of drug given they tested positive is only 22.8%
even though P(B/A) is high 99% It doesn't mean P(A/B) is high
