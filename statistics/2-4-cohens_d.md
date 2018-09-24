[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

This exercise asks us to compare Cohen's d, an effect size statistic, for two comparisons: the difference in pregnency length between first-born babies and others, and the difference in birth weight between first-born babies and others

Cohen's d for the difference in pregnency length between first-born babies and others is ~.0289; in other words, the difference in means is about .029 standard deviations.  (For comparisons' sake, the difference in height bewteen men and women is about 1.7 standard deviations).

Cohen's d for the difference in birth weight between first-born babies and others is ~ -.0887; in other words, the difference in means is about -.9 standard deviations.  

From these two Cohen's d stats, we can see that the difference in means between first-born babies and others in both pregnency length and birth weight are not very large, but that the effect of birth order on birth weight is larger than effect of birth order on pregnency length.

Python code for the numbers above is given below.  The module 'nsfg' is a dataset of birth records packaged in the 2nd Edition of ThinkStats.

'''{python}
import math
import numpy as np
import nsfg

#read in total dataset
preg = nsfg.ReadFemPreg()

#restrict dataset to live births
live = preg[preg.outcome == 1]

#split dataset into first births and other births
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

#function to calculate Cohen's d for the means between two groups
#input: two series		output: Cohen's d for the difference in means in the  two series
def CohenEffectSize(group1, group2):
    diff = group1.mean() - group2.mean()
    
    var1 = group1.var()
    var2 = group2.var()
    
    n1, n2 = len(group1), len(group2)
    
    pooled_var = (n1*var1 + n2*var2) / (n1+n2)
    
    d = diff / math.sqrt(pooled_var)
    
    return d
    
#define variables for pregencny length and birth order for first-born babies and others
firsts_preglngth = firsts.prglngth
others_preglngth = others.prglngth
firsts_totalwght = firsts.totalwgt_lbs
others_totalwght = others.totalwgt_lbs

#Cohen's d for pregnency length between first-born and other babies
CohenEffectSize(firsts_preglngth, others_preglngth)

#Cohen's d for birth weight (in lbs) between first-born and other babies
CohenEffectSize(firsts_totalwght, others_totalwght)
'''
