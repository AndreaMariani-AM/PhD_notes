
# Computational_Genomics
Topic: #ComputatinalBiology #Bionformatics #RNAseq 
Date: 2022-10-13

---

## Summary
Notes about [this meeting](https://www.youtube.com/watch?v=ucPBBTjH5EE) held at the *UCLA* by the [Institute for Pure and Appplied Mathematics](http://www.ipam.ucla.edu/) , talk by [Lior Pachter]((https://pachterlab.github.io/software.html)

## Notes
- *EXPERIMENTS THAT PRODUCE READS ARE INHERENTLY RANDOM, BECAUSE BIOLOGY IS RANDOM AND STOCHASTIC*
- *AT LEAST 6 BIOLOGICAL REPLICATES* for differential expression analysis, though isn't feasible money-wise. 
- There are different ways to produce *q-values* that are subletly different. A *theroretical* q value is given by:
	- rank in ascending order the p values, rank them from 1 to n, and calculate q values as $$\Large q_i = \frac{p_i \cdot N}{rank_i}$$
		so a corresponding p value times the total number of samples over the rank of the sample.
- [[Benjamini-Hochberg _Theorem]] controls *FDR* but cannot say anything about which memebr of the resulting list is a *false or true positive*. This is subtle but fondamental difference.

### Estimating sample mean and sample variance
-  Sample mean: $$\Large \overline x = \frac{1}{n} \sum_{i = 1}^{n} x_i$$
Which is just the *average* of you counts in this case

- Sample variance: $$\Large s^2 = \frac{1}{n -1} \sum^{n}_{i=1} (x_1 - \overline x_i)$$
	And a test for *Differential Analysis* is basically: given the mean of my two conditions (e.g. treated and untreated), these numbers are very *different* relative to the *variance* we're seeing.
- Tools like *DEseq2* and *edgeR* and similar tools have introduced very specific *statistics and methodologies* in genomics to examine *variance* and the reason is connected the concept (and how hard is to compute and estimate) *variance of the sample mean and variance of the sample variance*, in other words, what is the *variance of the estimator*. This has been an issue in the past and people in genomics have thought about this alot. Remember that the *variance* $\Large s^2$ or $\Large \sigma^2$ is the *square of the standard deviation*.
- *Variance of the sample mean*, suppose you draw $\Large n$ numbers at the time from a distribution that has a *true mean* $\Large \mu$, your gonna get different averages $\Large \overline x$ computed and what is gonna be the *variance* of those averages? *Variance $\Large s^2$ divided by $\Large n$ number of replicates*, cause the *more replicates* you have, the *less variance* you have of the *mean estimator*
- *Variance of the variance estimator*, goes like the *variance squared* divided by *roughly n*. To get a *resonable estimate* of the *variance* of $\Large n$ numbers it requires *more replicates that to estimate the mean*.
- *REPLICATES ARE FUNDAMENTAL TO BETTER ESTIMATE VARIANCE*



## Questions
- Item



