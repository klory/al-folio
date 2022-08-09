---
layout: post
title: Hypothesis test
description: 
date: 2022-07-28
comments: true
---

From [here](https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/): Hypothesis testing in statistics is a way for you to test the results of a survey or experiment to see if you have meaningful results. You’re basically testing whether your results are valid by figuring out the odds that your results have happened by chance. If your results may have happened by chance, the experiment won’t be repeatable and so has little use.

# Null Hypothesis
From [here](https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/) again: The null hypothesis is always the accepted fact.

# State a Null Hypothesis
This is a little tricky, you make a hypothesis based on experiment result, stating a null hypothesis means "assuming your result still follows the accepted fact", let's try [some exercises](https://www.statisticshowto.com/probability-and-statistics/hypothesis-testing/):

> [IQ expl] A principal at a certain school claims that the students in his school are above average intelligence. A random sample of thirty students IQ scores have a mean score of 112.5. Is there sufficient evidence to support the principal’s claim? The mean population IQ is 100 with a standard deviation of 15.

Here, the accepted fact is "IQ=100", the principle hypothesizes "IQ>100 in his school", so the null hypothesis is "IQ=100 in his school". And we are computing under the null hypothesis, how likely (probability) the result (IQ=112.5 over 30 students) will happen?

* Knows:
  * pupulation mean = 100
  * population std = 15
  * sample size = 30
  * sample mean = 112.5
  * sample std = ?
* Goal:
  * If the sample mean is significant

know population std => Z-test

---

> [Blood glucose expl] Blood glucose levels for obese patients have a mean of 100 with a standard deviation of 15. A researcher thinks that a diet high in raw cornstarch will have **a positive or negative** effect on blood glucose levels. A sample of 30 patients who have tried the raw cornstarch diet have a mean glucose level of 102.

Here, the accepted fact is "$$\mu=100$$", the researcher hypothesizes "$$\mu<100$$ or $$\mu>100$$ with cornstarch", so the null hypothesis is "$$\mu=100$$ with cornstarch". And we are computing under the null hypothesis, how likely (probability) the result ($$\mu>=102$$ or $$\mu<=98$$ over 30 patients, [why?](#oneside_vs_twoside)) will happen?

* Knows:
  * pupulation mean = 100
  * population std = 15
  * sample size = 30
  * sample mean = 102
  * sample std = ?
* Goal:
  * If the sample mean is significant

know population std => Z-test

---

> [Patient recovery expl] Researcher thinks that if knee surgery patients go to physical therapy twice a week (instead of 3 times), their recovery period will be longer. Average recovery times for knee surgery patients is 8.2 weeks, experiemnt result on 40 patients shows the average is 8.3 weeks and std is 0.5 weeks.

Here, the accepted fact is $$\mu=8.2$$, researcher hypothesizes "$$\mu>8.2$$ when therapy twick a week". So the null hypothesis is "$$\mu=8.2$$ when therapy twice a week". In other words, twice a week has no effect, the patients still only need 8.2 weeks to recover. And we are computing under the null hypothesis, how likely (probability) the result (8.3 weeks over 40 patients) will happen?

* Knows:
  * pupulation mean = 8.2
  * pupulation std = ?
  * sample size = 40
  * sample mean = 8.3
  * sample std = 0.5
* Goal:
  * If the sample mean is significant

do NOT know population std => T-test

---

Now let's try more:

> [[Toss coin expl](https://www.probabilitycourse.com/chapter8/8_4_4_p_vals.php) expl] If we toss a coin 100 times with 60 heads, can we trust it to be a fair coin?

Here, the accepted fact is "coin is fair", the computed result hypothesizes "This coin is not fair with P(head)=0.6", so the null hypothesis is "This coin is fair". And we are computing under the null hypothesis, how likely (probability) the result ($$P(head)=0.6$$) will happen?

* Knows:
  * pupulation mean = np = 100 * 0.5 = 50
  * population std = $$\sqrt{np(1-p)} = \sqrt{100 * 0.5 * 0.5} = 5$$
  * sample size = 100
  * sample mean = 60
  * sample std = $$\sqrt{100 * 0.6 * 0.4} \approx 4.9$$
* Goal:
  * If the sample mean is significant

know population std => Z-test

---

> [[Pearson expl](https://docs.scipy.org/doc/scipy-0.14.0/reference/generated/scipy.stats.pearsonr.html) expl] Given two sequence x (feature) and y (label), we can compute [Pearson correlation](https://en.wikipedia.org/wiki/Pearson_correlation_coefficient) r. Assume r is high (e.g., 0.8), how do we trust this result, what if both sequences are actually randomly sampled and this is just a coincidence? In other words, how to know if this result is **significantly** different compared with "assuming x and y are randomly sampled"? How **confident** are we about the result?

Here, the accepted fact is "if data are randomly sampled, they should have no correlation, in other words, the pearson correlation coeeficient should be $$r_0=0$$", the computed result hypothesizes "This {x,y} have correlation $$r_{x,y}=x$$", so the null hypothesis is "This {x,y} have no correlation". And we are computing under the null hypothesis, how likely (probability) the result ($$r_{x,y}==x$$) will happen?

* Knows:
  * pupulation mean = 0
  * population std = ?
  * sample size = len(x) + len(y) - 2 ([why?](https://stats.stackexchange.com/questions/270612/why-test-statistic-for-the-pearson-correlation-coefficient-is-frac-r-sqrtn-2))
  * sample mean = r
  * sample std = $$\sqrt{1-r^2}$$ ([why?](https://stats.stackexchange.com/questions/270612/))
  
* Goal:
  * If the sample mean is significant

know population std => T-test

---


> [[Two independent sample mean](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.ttest_ind_from_stats.html) expl] We are given two sequence a and b which may be sampled from the same one-dimensional random variable. E.g., we get 13 samples in a~[1, 3, 4, 6, 11, 13, 15, 19, 22, 24, 25, 26, 26] and 11 samples in b~[2, 4, 6, 9, 11, 13, 14, 15, 18, 19, 21], can we trust their means are actually the same?

Here, the accepted fact is "if two sequence are sampled from same random variable, they should have identical mean", the computed result hypothesizes "These two sequences {a,b} are not from the same random variable, and their mean differenc is $$\Delta$$", so the null hypothesis is "These two sequences {a,b} are sampled from same random variable". And we are computing under the null hypothesis, how likely (probability) the result (mean difference is $$\Delta$$) will happen?

* Knows:
  * pupulation mean = 0 (assume identical mean)
  * population std = ?
  * sample size = len(x) + len(y) - 2 ([why?](https://en.wikipedia.org/wiki/Student%27s_t-test#Independent_two-sample_t-test))
  * sample mean = $$\bar{a} - \bar{b}$$
  * sample std is quite complex, check the wikipedia for ([why](https://en.wikipedia.org/wiki/Student%27s_t-test#Independent_two-sample_t-test))
  
* Goal:
  * If the sample mean is significant

---

Now let's try more and more:

> [Classification expl] You develop a binary classification model with accuracy 98%, can you trust this accuracy?

Here, the accepted fact is "if we randomly guess the result, we will have an accuracy 50%", the reuslt hypothesizes "This is not random guess (the model works)", so the null hypothesis is "This is still random guess". And we are computing under the null hypothesis, how likely (probability) the result (accuracy is 90%) will happen?

---

> [Regression expl] You develop a regression model which has mse (mean squared error) 0.2, can you trust this mse?

Here, the accepted fact is "if we randomly guess the result, we will have an mse $$err_0$$", the reuslt hypothesizes "This is not random guess (the model works)", so the null hypothesis is "This is still random guess". And we are computing under the null hypothesis, how likely (probability) the result (mse is 0.2) will happen?

# Conclusion
We now understand what is null hypothesis and how to state it. And at the end of each example, I also throw out a question, the question is actually what z-test/t-test tries to answer, more generally, **under null hypothesis, how like the result will happen?**

I'll explain more in following posts.
