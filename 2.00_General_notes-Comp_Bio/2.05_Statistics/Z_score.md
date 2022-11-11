
# Z_score
Topic: #Zscore #Scaling #Normalization #RNAseq 
Date: 2022-11-09

---

## Summary
*Z score* is a general purpose score that  *relates one sample's score* to the *mean*  in a group of scores. In other words is the number of *standard deviations* by which a r*aw score* is *above* or *below* the *mean value* of what is being observed

## Notes
- Useful links/discussions:
	- [stackExchange](https://bioinformatics.stackexchange.com/questions/2180/rnaseq-z-score-intensity-and-resources) and [stackExchange2](https://stats.stackexchange.com/questions/36076/is-a-heat-map-of-gene-expression-more-informative-if-z-scores-are-used-instead-o), [Research Gate](https://www.researchgate.net/post/How-can-I-calculate-z-score-from-rpkm-or-counts-values), [biostar](https://www.biostars.org/p/356041/)
- An intuitive examples is:
	- A z-score of -3 for the *gene X in sample A* means that this value is *3 sd lower* than the *mean of the values for gene X in all the samples* (A, B, C ...). If a gene is *differentially expressed* then it's z-score will be *mostly positive* in one group and *mostly negative* in the other.
- Z-score have to be calculated on *approximally normally distributed data*. Usually *TPM/FPKM* aren't normally distributed, so taking the *Log2* should make then *approximatley* normal. Otherwise it'll be misleading. Raw counts also *aren't normally distributed* (usually are *negative binomial*). Doing *Rlog* transformation should make them *approximately* normal.
## Questions
- Item



