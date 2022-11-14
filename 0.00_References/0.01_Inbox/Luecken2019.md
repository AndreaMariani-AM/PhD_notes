# Luecken2019
Full title: *Current best practices in single-cell RNA-seq analysis: a tutorial*
Authors: *Malte Luecken* (first); *Fabian Theis* (last)
Year: *2019*
Topic: #SingleCell #RNAseq #ComputatinalBiology 
Journal: *Molecular Systems Biology*
DOI: https://doi.org/10.15252/msb.20188746
Date: 2022-10-21

---

Source: The original source of the document can be found [here](https://www.embopress.org/doi/full/10.15252/msb.20188746?cookieSet=1)

---

## Summary
This is a note on best practises in *scRNAseq* analysis, a paper by [Fabian Theis](https://backup.helmholtz-munich.de/icb/research/groups/machine-learning/overview/index.html).
Most of the info that i'll present for the single cell lecture are taken from here. *scRNAseq has enable gene expression to be studied at an unprecedent resolution* and effectively tackle the *heterogenic systems*.

## Notes
- Common steps:
	- *Pre-processing* : *quality control*, *normalization*, *data correction*, *feature selection* and *dimensionality reduction*
	- *Cell-* and *gene-level* downstream analysis.
- A major problem is the *lack of standardization* due to the relative *immaturity* of the field. *Main challenges* are *increasing number of analysis methods* and *dataset sizes*.
- The choice of language *R or Python* usually means the choice of most *methods* (think about *Seurat and Scanpy*).
- Steps that happen before *Count matrix*:
	- Single cell *isolation*, either *plate based* or *droplet based*. Droplet based methods capture each cell into its own *microfluidic droplet*. Multiple cells captured together -> *Doublets or Multiplets*, no cells captured or non viable cells -> *empty droplets/wells*. *Empty droplets* are very common for *droplet based method* given that they rely on a low concentration flow of input cells to control *doublet rates*.
	- Each droplet contains the necessary chemicals to *break down* the cellular membrane and *perform* library construction. Given that these processes happen for cells in isolation it's possible to *label* each droplet with a *specific barcode*. Also, many experient label the molecule with a *Unique Molecular Identifier* (*UMI*). cDNA is amplified before sequencing.
	- *UMI* allows us to distinguish between *amplified copies of the same mRNA molecule and reads from separate mRNA molecules transcribed from the same gene*.
- Main start and also what is the *gold standard* as *raw data* for scRNAseq is *Read/Count matrix*. *Count matrix* is when UMis have been incorporated. Resulting matrix have the dimensions *number of barcodes* x *number of transcripts*.
		- *barcode* instead of *cell* because all reads assigned to the same barecode may not correspond to reads from the same cell (tagging more cells --> *doublets*)

#### Pre-processing
- To ensure that all *cellular barcode* data correspond to *viable cells*.
- Usually done on three main *covariates*:
	- 1) *Number of genes per barcore*
	- 2) *Number of counts per barcode*
	- 3) *Fraction of counts from mitochondrial gene*
	Two classic examples are: 
		- barcodes with *low* count depth and *few* gene detected + *high* fraction of mito genes = cells with cytoplasmic mRNA that has leaked through a broken membrane and mito genes are intact. 
		- Cells with *unexpectedly high* counts and genes detected are probably doublets.
- *CONSIDERING ANY OF THESE THREE COVARIATES IN ISOLATION CAN LEAD TO MISINTERPRETATION OF SIGNALS* and in general thresholds should be as permissive as possible to avoid filtering out cell populations unintentionally.
- *QC* at the *level of transcripts* involve the reduction of transctripts detected (~ 20k) by filtering out *genes* that *are not expressed* in at least X number of cells, thus not informative of the *cellular heterogeneity.*
- *Ambient gene expression or contamination* referes to counts that *do not originate* from a barcoded cell but from other *lysed cells* whose mRNA have contaminated the library prep. In droplet based dataset this can be corrected by *modeling* ambient RNA expression profiles from *empty droplets*, which are abundant in this technology.

#### Normalization
- For each count in a count matrix, lots of steps are performed and difference in *identical* cells can be due just to *sampling* efffects. Most commonly used is *count depth scaling* also referred to as *CPM*, but very old
- *Linear Global scaling*:
	- *CPM*
	- *CPM* that exclude genes that account for at least 5% of the total counts per cell
	- *Scran pooling based* size factor estimation using a *linear regression* over genes. Top performer and also works great for *batch effect correction* and *differential analysis*.
- *Non Linear normalization* can account for more complex unwanted variation:
	- *Parametric modelliing* of count data
	- *Others*
	-In general, *non-linear* methods outperform *linear* methods especially where strong *batch effect* is present.
- Typically after nromalization, data matrices are  $\large log(x +1)$ transformed
## Reference to chek out

## Cited by
```query

```

## Index
[[00_Index_papers^]]