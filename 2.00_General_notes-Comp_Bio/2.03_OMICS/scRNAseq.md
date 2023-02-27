
# scRNAseq
Topic: #SingleCell #RNAseq #ComputationalBiology 
Date: 2022-11-04

---

## Summary
These are random notes on *scRNAseq* that i can find online and when i face some problems.

## Notes
- With *scRNAseq* you can *estimate the distribution expression levels* for each gene across cells, while you cannot do it with *Bulk RNAseq*, where you get a single expression value for each gene.
- Two main types of *transcript quantification*: 
	-  *Full lenght*: try to achieve full length coverage, usually 3' bias, accumulation at the end of the gene body.
	- *Tag based*: Only 3' or 5' can be sequenced, can be paired with *UMI* -> improved accuracy of transcipt quantification. Downside is that, given it's not full lenght, it reduceses our aibility to *unambiguously* align reads to a transcript and discriminate different isoforms.
- *Dropout effect*: a dropout is a gene that is expressed in a cell but we couldn't detect it.   Or gene dropout is when a gene is detect in a cell but not in the other, even if it should have.
- 3 Key information are generated:
	- *cDNA fragments* that identify the RNA transcripts
	- *Cell barcode*, identifies the cell where the RNA was expressed
	- *UMI*, allows to collapse reads that are PCR duplicates
- Classical workflod:
	- *Mapping cDNA* fragments to reference
	- *Assign reads to genes*
	- *Assign reads to cell* --> *Cell Barcode Demultiplex*
	- *Counting number of unique RNA molecules* --> *UMI deduplication*
- Library of Unique *Cell Barcodes* attached to the beads that identify individual cells si called *Whitelist*, and depends on the Kit used
- *UMI counting* consists of *read counting* followed by *PCR duplicate collaps* baes on UMI sequences.

- Expression data is usually stored as a *feature-by-sample matrix* of expression quantification.

## Resources
- [Single cell course Hemberg Lab](https://www.singlecellcourse.org/index.html)
- [Single cell course Liu Lab](https://liulab-dfci.github.io/bioinfo-combio/scrna1.html)
- [Transcriptomics course](https://github.com/SingleCellTranscriptomics/ISMB2018_SingleCellTranscriptomeTutorial)
- [Broad Institute course](https://broadinstitute.github.io/2020_scWorkshop/)



