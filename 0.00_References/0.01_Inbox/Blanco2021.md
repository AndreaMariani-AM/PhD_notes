# Blanco2021
Full title: *SpikChIP- a novel computational methodology to compare multiple ChIP-seq using spike-in chromatin*
Authors: *Enrique Blanco* (first); *Sergi Aranda* (last)
Year: *2021*
Topic: #ComputatinalBiology #Chromatin #ChIPseq #Spikein
Journal: *NAR Genomics and Bioinformatics*
DOI: https://doi.org/10.1093/nargab/lqab064
Date: 2022-06-27

---

Source: The original source of the document can be found [here](https://academic.oup.com/nargab/article/3/3/lqab064/6329082)

---

## Summary
ChIPseq is inherently semi-quantitative (relative occupancy of a factor in a location with respect to the rest of the genome) given that it lacks a reference for the control of biological and experimental variabilities. *Blanco et al.* propose a method that exploits a reference exogenous genome (*Spike-in or ChIP-Rx from Orlando et al 2014*, or [[Bonhoure2014]]) across samples in a genome-wide manner by using a [[Local_regression]] strategy *SpikChIP*. Compared to other methods it reduces the influence of sequencing noise of Spike-in chromatin during ChIPseq normalization, while minimizing the overcorrection of non-occupied genomic regions in the experimental ChIP-seq. Code availabe on [GitHub](https://github.com/eblancoga/spikChIP).
## Notes
- Critiques to *Orlando et al* and *Bonhoure et al*: 
	- Spike-in reads mapped to enriched regions (Peaks) and also non-enriched background regions are used to calculate normalization factor
	- Correction factor is uniformly applied to all experimental reads, treating both specific and non loci in the same way
	- Removal of informative reads impacts genomic coverage and downstream analyses
- [[Guertin2018]] proposed a new method using a liner local regression and *Blanco et al* exploit their idea
- *Advantages* they propose:
	- Normalizes ChIPseq signal over the complete genome
	- Minimize the influence of background regions, though dominating over the total number of reads, when computing a scaling factor.
	- It's not applied uniformely, instead, it's applied increasingly and gradually from the backgrounf to positive ChIP signal regions.

## Reference to chek out



## Cited by
```query

```

## PDF Preview
![[SpikChIP- a novel computational methodology to compare multiple ChIP-seq using spike-in chromatin.pdf]]


