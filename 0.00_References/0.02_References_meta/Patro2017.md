# Patro2017
Full title: *# Salmon provides fast and bias-aware quantification of transcript expression*
	Authors: *Rob Patro* (first); *Rafael Irizarry & Carl Kingsford* (co-last) (+  *Micahel Love*)
Year: *2017*
Topic: #ComputatinalBiology #RNAseq #Quantification 
Journal: *Nature Methods*
DOI: https://doi.org/10.1038/nmeth.4197
Date: 2022-09-05

---

Source: The original source of the document can be found [here](https://www.nature.com/articles/nmeth.4197)

---

## Summary
Salmon is a lightweight method for *quantifying* transcript abundance in RNAseq experiments. Uses a *dual-pahse parallel inference algorithm* and *feature-rich bias* model combined with an *ultra-fast* read mapping procedure. First transcriptome-wide quantifier that corrects for *fragment GC-content bias*, yielding more *accurate* abundancy estimates and *sensitivity* of downstream *DE* analyses.

## Notes
- Most *transcriptome-wide* aligners both *aligner-dep and indep* lack sample-specific bias  models rich enough, here they introduce a way to caputre *GC-content bias*.
- Salmon has 3 main parts:
	- *Light-weight* mapping model
	- *Online phase* that estimates initial abundacies and model parameters
	- *Offline phase* that refines expression estimates
- The *two-phase* inference procodure alllows Salmon to build a probabilistic model of the sequencing experiment. Can either map reads by itself by a fast a lightweight procedure called *quasi-mapping*[[Quasi-mapping]]
- or accepts precomputed *SAM/BAM*
- Unlike *pseudoaligners*, Salmon tracks *position* and *orientation* of all mapped fragments and in conjunction w/ abundancies form *online inference* to compute a *per-freagment conditional probabilities* rather than a normal *transcript compatibility*. These probabilities are to estimate *auxiliary models* and *bias terms* to update abundance estimates.
- More accurate than *Kallisto* improves *inter-replicate concordance* that produces a higher sensitivity when used for *DE* analyses.
- Salmon *rich-model* can account for effects of *sample-specific* parameters and biases typical of RNAseq:
	- *positional* biases in coverage
	- *sequence-specific* biases at *5' or 3 ends'*
	- *Fragment-level GC* bias
	- *strand-specific* protocol
	- *fragment-length* distribution

## Reference to chek out

## Cited by
```query

```

## Index
	[[00_Index_papers#^1faca1]]