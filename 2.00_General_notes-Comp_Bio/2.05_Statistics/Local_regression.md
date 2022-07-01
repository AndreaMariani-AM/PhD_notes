
# Local_regression
Topic: #Statistics #Math #ComputatinalBiology 
Date: 2022-06-29

---

## Summary
This note contains info on local regression (also called *local polynomial regression*). Concept found in [[Blanco2021]] (*SpikChIP*).
A good resource is the [book](https://rafalab.github.io/pages/754/section-03.pdf) from Rafael Irizzary @[rafalab](https://rafalab.github.io/)

## Notes
- In contrasts to canonical [[Linear_Regression]], Local Regression cna apply fitting models to particular subsets or segments of the data, identified by [[k-nearest-neighbor]].
-  Used to model a relation between a predictor variable and a response variable. A simple fixed model would be:
$Yi = f(xi) + \epsilon i$
where $f(xi)$ is an unknown function and $\epsilon i$ is an error term representing random error/variability not accounted by $xi$. We assume $\epsilon i$ have mean = 0 and variance $var(\epsilon i) = \sigma^2$ 
- We make no global assumption of $f$ but asume that locally can be well approximated by simple parametric function (e.g constant or straight line).
- Generazation of the *moving average* and *polynomial regression*, for this is also known as *moving regression*. 
- Developed initally for *scatterplot smoothing*, it's most common methods are
	- *LOESS*: Locally estimated scatterplot smoothing 
	- *LOWESS*: Locally weigthed scatteplot smoothing
These are two strongly related *non-parametric* regression methods that combine multiple regression in a k-nearest-neighbor-based meta-model. Build upon "classical" linear and non linar regression.
- Visual example [here](https://www.google.com/search?q=loess+statistics&rlz=1C5GCEM_enIT1012IT1012&source=lnms&tbm=isch&sa=X&ved=2ahUKEwilmd_M_dT4AhWm_bsIHUAgBOUQ_AUoAXoECAIQAw&biw=1895&bih=948&dpr=1#imgrc=HCVaYSXVrTDPoM).
- Main benefits:
	- Fitting a line to a scatter plot where noisy data values, sparse data points or weak interrelationships interfere with your ability to see a line of best fit.
	- Linear regression where [least squares fitting](https://www.statisticshowto.com/probability-and-statistics/statistics-definitions/least-squares-regression-line/#LSFitting) doesn’t create a line of good fit or is too labor-intensive to use.
## Questions
- Item
