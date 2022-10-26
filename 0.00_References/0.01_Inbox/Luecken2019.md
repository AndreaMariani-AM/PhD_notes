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
- Main start and also what is the *gold standard* as *raw data* for scRNAseq is *Read/Count matrix* 
## Reference to chek out

## Cited by
```query

```

## Index
[[00_Index_papers^]]