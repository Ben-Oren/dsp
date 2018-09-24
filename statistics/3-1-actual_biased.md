[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

The mean of the 'actual' distribution of kids per household in the respondents dataset is 1.024

The mean of the 'observed' disribution of kids per household in the respondents dataset is 2.404 

We see this discrepancy because of the bias in surveying kids: the households with no kids can't show up in the 'observed' distribution, and the households with more kids are more likely to be sampled

The python code for calculating those means and generating PMF plots is below.  The modules nsfg and thinkstats2 are bundled at the ThinkStats link above

'''{python}

import nsfg
import thinkstats2

#read in data
data = nsfg.ReadFemResp()

#create dict of [number of kids]:number of respondents with that number of kids
#variable 'numkdhh' is number of kids in respondent's household
kids_dict = {}
for resp in data.numkdhh:
    kids_dict[case] = kids_dict.get(case, 0) + 1
    
#create unbiased and biased PMFs based on values in kids_dict
#unbiased pmf is just number of kids in hh * %age of respondents with that number of kids; uses class built in thinkstats2 
pmf_unbiased = thinkstats2.Pmf(kids_dict, label = 'actual')

#biased pmf multiplies each probability in the unbiased PMF by the number of kids in the hh that would observe that probability, again using class bulit in thinkstats2
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label = label)
    
    for x, p in pmf.Items():
        new_pmf.Mult(x,x)
        
    new_pmf.Normalize()
    
    return new_pmf
    
pmf_biased = BiasPmf(unbiased_pmf, 'observed')

#we can now get the means and graphs of the pmfs of actual and observed number of kids in each household of the respondent dataset 

print('unbiased pmf,', pmf_unbiased.Mean())
print('observed pmf,', pmf_biased.Mean())

thinkstats2.thinkplot.PrePlot(2)
thinkstats2.thinkplot.Pms([pmf_unbiased, pmf_biased])
thinkstates2.thinkplot.Show(xlabel = 'kids in hh', ylabel = 'PMF')
'''




