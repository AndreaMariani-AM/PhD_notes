
# Logarithm
Topic: #ComputatinalBiology #Bionformatics #Math 
Date: 2022-06-17


---

## Summary
Notes on Log transformation and its implications

## Notes
* Why the -log10(pvalue): we use -log10(pvalue) in various occasions. usually doesn't matter what kind of base you take for the log tranformation, but generally base 10 it's easier to interpret. Taking the Log shrinks differencies at the high end and increase differences at the low end. Logs also allow exponential behaviour to be seen in a linear manner. The reason we use -log is that, for example in a volcano plot, we can show "highly significant" (very low pvalue) genes at the top of the graph. So, the lower the pvalue, the "higher" would be the -log10(pvalue), the "higher" would be in the graph. With this we can show graphically which genes have a very low pvalue.
* Why the log2(value): usually, taking the log of a value it's the log2(value) it's useful for a variety of reason:  1) Log transformed values makes the modelling *PROPORTIONAL* to changes rateher than *ADDITIVE*. This is tipically  biologically more relevant. 2) errors are usually proportional to the values, relationship that's absent on the log scale. 3) Matter of taste, a doubling or reduction of 50% is translated as a +1 or -1, easy to remember and visualize (for a log10 id +- 0.3).

## Questions
- Item



