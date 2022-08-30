
# Salmon_RNAseq
Topic: #RNAseq #GeneExpression #Quantification
Date: 2022-08-29

---

## Summary
This is a note where i share why i'm thinking about going for an aligner-free software for gene quantification rather than our standard approach (STAR + featureCounts). Probalby i'll update the pipeline to use Salmon as default and leave a rule to use START + featureCounts if needed.
[Salmon paper](https://www.nature.com/articles/nmeth.4197)

## Notes
- [Salmon documentation](https://salmon.readthedocs.io/en/latest/) and [Github page](https://github.com/COMBINE-lab/salmon)and [Tutorial](https://combine-lab.github.io/salmon/getting_started/)
- Some references here:
	- [Why you should use alignment-independent quantification for RNAseq](https://cgatoxford.wordpress.com/2016/08/17/why-you-should-stop-using-featurecounts-htseq-or-cufflinks2-and-start-using-kallisto-salmon-or-sailfish/)
	- [Comparison Salmon/Kallisto vs STAR+HTSeq](https://crazyhottommy.blogspot.com/2016/07/comparing-salmon-kalliso-and-star-htseq.html)
- Our workframe has always been: *Align to the reference genome and then count reads aligning  to genes us featureCounts*. With *Alignment-independent* software one can count reads per transcripts and the aggregate the gene-level counts to feed it to DEseq2/edgeR.

###### Gene level
- *featureCounts* underestimates the abundance of gene with less than 90% unique sequence, and that happens cause the software ignore reads that could be assigned to multiple genes. This understimation shouldn't be a problem as long as it's consistent between samples, given that the fraction of unique sequence for a given gene doesn't vary.
- *Alignment-free* methods, *Kallist, Salmon and Sailfish*, outperform *alignment-dependent* methods for genes that have <80% unique sequence (~ 11% of all genes).  No detectable difference between the three *alignment free* method

###### Trascript Level
- As expected, correlation between *ground truth* vs *expression estimates* is much worse at transcript-level than gene-level, because of the reduction in unique sequences.
- Again, *alignment-free* methods are clearly more accurate for transcripts w/ <80% unique sequence (~ 96% trascripts).
## Questions
- Item



