
# HiC_pipeline
Topic: #HiC #ChromatinConformationCapture #Chromatin #ComputatinalBiology 
Date: 2022-07-22

---

## Summary
This is a note on my HiC pipeline written in snakemake. It'll will comprise info on softwares (redirected to their own note) and procedures, best practises and so on. Also relevant papers will be linked to this note.

## Notes
- I will exploit this review [here](https://link.springer.com/content/pdf/10.1007/s12551-018-0489-1.pdf), note [[Pal2018]] , and the pipeline present on the [n-core](https://github.com/nf-core/hic) website and [snakemake](https://github.com/maxplanck-ie/snakepipes).
- Two major steps: From *fastq* to *contact matrix* and *downstream analyses*.

## Tools and Pakcages
- *HiC-Pro* for data processing
- *Bowtie2*[[Aligners#^ed3b6d]] or *bwa* for alignment 
- *deDoc*? for bin size selection.
- *ICE* (*Cooler*) for normalization and generation of contact maps.
- *Juicer*, *CscoreTool*, *HOMER*, *HiTC*, *cooltools*, are some of the softwares that can be used to call compartments.
- *Cworld*, *HiCseg*, *ClusterTAD*, *TADbiT*, *HiCBricks*, *HiCExplorer*, *cooltools* are some softwares for TADs calling.
- *GOTHiC*, *HIPPIE*, *HOMER*, *HiCCUPS* are some software to identify interacions/chroamatin loops.
- Some common pipelines are: 
	- [ICE]()
	- [TADbit](https://github.com/3DGenomes/TADbit)
	- [HiCUP](https://www.bioinformatics.babraham.ac.uk/projects/hicup/)
	- [HIPPIE](https://github.com/yihchii/hippie)
	- [Juicer](https://github.com/aidenlab/juicer)
	- [HiC-Pro](https://github.com/nservant/HiC-Pro)
	- 

## Steps FASTQ to Contact Matrix
1) *Alignment* to the reference genome. *PE reads* are aligned separatly, single-end mode, given the nature of this data cause they usually map to very different location. There might be problems if the read span the ligation junction, thus the read having two portions of the read mapping to distinc genomic location. This generates *chimeric reads* and different approaches have been developed.
2) *Filtering* of spurious signal. This is *extremely* important for this type of technique. Removal of *PCR* duplicates of *low quality* alignment. Filtering on *distance* between the mapped read and the downstream restriction size, to see if it's compatible with expected fragment size.
3) *Binning* read counts. Bins are continous partitioning of the genome in intervals of fixed size. They allow achieve a more robust and less noisy signal estimation of contact frequencies, at the expense of resolution. Rule of thumb for bin size:  ```having at least 80% of bins covered by 1000 reads```. *deDoc* is used to select the optimal bin size at which the structural entropy of the HiC matrix reaches a stable minimum.
4) *Normalization*. Has two main types:
	1) *Explicit* normalization. Based on explicit definition of know *biases* (fragment lenght, GC%, ...), correction factors are compute for each bias alone and in combination and then appplied to reads count in each bin.
	2) *Implicit* or *matrix-balancing* normalization. Relies on the assumption that each genomic locus should have *equal visibility* and the interaction singal should add up to the same total amount. Uses *sequential component normalization* (SCN) or *Iterative Correction and Eigenvector decomposition* (ICE) or *Knight-Ruiz matrix-balancing*.
Binning and normalization can be done simultaniously.
After Binning and normalization i have a *Contact Matrix*

## Steps Downstream analyses
Every analysis that is designed to extract a biological meaningful result from HiC data matrices at multiple level of resolution.  
1) *Identification Compartments*. Different algorithms and methods one can use. Extensively review by [Miura et al.](Practical analysis of Hi-C data: generating A/B compartment profiles) Using *Pearson correlation* of the distance normalized matrix. ^04610d
2) *TADs Calling*. Uses a *Directionality Index (DI)*, or an *Insulation Score* or *Partitioning and/or Clustering algorithm*. ^62ce37
3) *Identification of Points of Interaction* or *Loop Calling* (loop only if is cis-interaction) ^636b7a



