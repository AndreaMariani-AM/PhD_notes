
# Normalization
Topic: #ComputatinalBiology #Bionformatics #Normalization
Date: 2022-06-17


---

## Summary
Notes on Normalization strategies and thei interpretation

## Notes
* Whithin sample normalization: Necessary to compare gene expression between different conditions. Caveats to be assed: library size(i.e. seq depth), length of the gene, library composition(i.e. relative size of studied transcriptome), GC content bais, read coverage of a transcript con be non-uniformly distributed alonf the transcript. Most normalization address library size. *[[2.00_General_notes-Comp_Bio/2.05_Statistics/change_me]] CPM(counts per million)* are obtained by dividing each gene's read count by a certain value and multyplying it by 10^6. *RPKM/FPKM(reads/fragments per kilobase per million reads)* and *TPM(transcripts per million)* are popular metric that improve upon *CPM*. *RPKM* is obtained dividing *CPM* by the length of the gene per kilobase. *FPKM* is the same as *RPKM* but it's used for paired-end reads. These first account for sequencing depth and then for gene lenght. *TPM* does the same but in the reverse order. First it'll normalize for gene length (per kilobase) and then gene-length normalized values are divided by the sum of normalized gene-length values and multiplied by 10^6. Thus the sum of normalized vlaues for *TPM*  will always be equal to 10^6 for each library. 
* Relative Log Expression (RLE) plot: They can be used to assess whether data needs more normalization even after DESeq normalization.
* Coverage :  1X coverage = read length * number of uniquely mapped reads / 3e+09.  A minimum coverage of 30X requires the average read depth across the genome to be 30 reads per base


## Questions
- Item



