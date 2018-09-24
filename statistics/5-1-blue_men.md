[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

About 34.3% of the population meets the heigh requirements to be a Blue Man (between 5'10'' and 6'1'')

To calculate this: I first transformed the heights from inches to cm, which is multiplying the height in inches by 2.54

Then, taking advantage of the fact that male heights roughly follow a normal distribution with mu = 178cm and var = 7.7, I looked up the percentile rank in a normal distribution with those parameters for the two heights.  This gives the percentage of the male population that is equal to or below the two values.

Finally, to find the percentage of the population that falls between the two values, I simply subtracted the percentile rank of 5'10'' from the percentile rank of 6'1''.  This gives the percentage of the distribution that lies bewtween the two values.

Python code to calulate the above is listed below.  

'''{python}
import scipy

#find the low and hi heights listed in inches in terms of cm
l_ht = (5*12+10) * 2.54
h_ht = (6*12+1) * 2.54

#use the CDF function in scipy to find the percentile rank for both l_ht and h_ht
l_pr = scipy.stats.norm.cdf(l_ht, 178, 7.7)
h_pr = scipy.stats.norm.cdf(h_ht, 178, 7.7)

#finally, subtract the percentile ranks from each other to find the %-age of the distribution between them

print(h_pr - l_pr)
'''

 