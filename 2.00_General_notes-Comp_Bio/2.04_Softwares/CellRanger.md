
# CellRanger
Topic: #SingleCell #10XGenomics #Transcriptomics #RNAseq 
Date: 2023-01-19

---

## Summary
This note contains info on how to use [cellranger software](https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/what-is-cell-ranger)

## Notes
- Usually when doing using [10x Chromium](https://www.10xgenomics.com/instruments/chromium-family) you can expect:
	- *Read 1* is usually *Cell Barcode + UMI*
	- *Read 2* contains the actual *transcript sequence*
- A multi CSV config file is necessary, this one points to *FASTQs* and has other parameters from the *cellranger multi* pipeline. [Full list of parameters](https://support.10xgenomics.com/single-cell-gene-expression/software/pipelines/latest/using/multi#multi-gex-cellplex-one)

## Questions
- Item



