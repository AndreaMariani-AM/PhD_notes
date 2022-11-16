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
- Overall *goal* of normalization is to remove *effects of count sampling*
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

#### Data Correction and Integration
- Data correction tries to remove *unwanted variability* that might be there even after *normalization*. Main targets are *technical and biological covariates* like `batch` ,`droput` and `cell cycle` effects.

##### Regressing out Biological effect
- Correction of biological covariated has the goal of single out paticular biological signals of interest. To remove *cell cycle* effects on the transcriptome, you can either simply fit a *linear regression* against cell cycle scores as implemented in [Scanpy]() or [Seurat](), or use complex mixture models such as [scLVM]() or [f-scLVM](). 
- *Marker genes* are retrieved form literature.  Same idea for regression out *mitochondrial gene expression*. 
- Can improve inference of *developmental trajectories* but can mask some true biological signal when studying *proliferating populations*.
 
##### Regressing out Technical effect
- Variants of *regression models* used for biological effects can be used to regress out technical effect. Most prominent *covariates* are *count depth and batch effect*.
- Normalization scales genes to be *comparable between cells* but doesn't affect *count depth*. When correcting for multiple covariates, regression should be performed *over all covariates at the same time* to accoutn for *dependence* between covariates
- An alternative is to use more robust methods like *downsampling or non linear normalization procedures.*

##### Batch effect and Data integration
- Applied to correct for effects that can arise when cells are handled in distinct groups like: Different *chips/lanes*, cells harvested at different *time points*. These can have an impact on the measurement of the transcriptome or directly influencing it.
- Correcting for batch effects between *samples or cells* in the *same experiment* is referred to *batch correction*. Correcting for batch effects between *multiple experiments* (same or different labs) si referred to as *data integration*. 
- [ComBat]() is great for batch correction
- [CCA](), [MNN](), [Scanorama](), [scGen](), [BBKNN]() and [Harmony]() are methods for data integration.
- `Be wary of over-correction given the increased degree of freedom of non-linear data integration approaches`.

##### Expression Recovery
- Also called *Denoising or imputation*. No consensus on whether we should use it or not. Be very careful
- It might be useful for *visualization purposes* but should be avoid when *generating hypothesis* duign *EDA*.

#### Feature Selection, Dimensionality Reduction and Visualization
- *Human and Mouse genomes* RNAseq datasets can contain expression values for > 20K genes. Most of these genes are *not informative* and many genes will mostly contain zero values, it's very *sparse matrix*. Even after *Qc* a significant number of genes is retained. To ease *computational burden* of downstream analysis, reduce *noise* in the data, and *visualize* it, some appreaches to *reduce the dimensionality* of the dataset exist.

##### Feature Selection
- Commonly the first step. It Filters the dataset to keep only the genes that are *"Informative"* of the variability in the data.
- *HVG*, Higly variable genes, are often used and depending on the task at end, ~1 to 5K of gene are usually kept. A simple method to select them is implemented both in *Seurat* and *Scanpy*. and consists of binning the genes based on their mean expressio and only the genes with the *highest variance-to-mean ration* are selected. Optimally they should be selected after *technical data correction*, to avoid selecting genes highly variables only due to  e.g. batch effects

##### Dimensionality Reduction


## Reference to chek out
## Cited by
```query

```

## Index
[[00_Index_papers^]]