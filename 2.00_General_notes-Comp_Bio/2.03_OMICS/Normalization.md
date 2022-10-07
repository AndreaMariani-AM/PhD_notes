
# Normalization
Topic: #ComputatinalBiology #Bionformatics #Normalization
Date: 2022-06-17


---

## Summary
Notes on Normalization strategies and thei interpretation

## Notes
* Whithin sample normalization: Necessary to compare gene expression between different conditions. Caveats to be assed: library size(i.e. seq depth), length of the gene, library composition(i.e. relative size of studied transcriptome), GC content bais, read coverage of a transcript con be non-uniformly distributed alonf the transcript. Most normalization address library size. *CPM(counts per million)* are obtained by dividing each gene's read count by a certain value and multyplying it by 10^6. *RPKM/FPKM(reads/fragments per kilobase per million reads)* and *TPM(transcripts per million)* are popular metrics that improve upon *CPM*. *RPKM* is obtained dividing *CPM* by the length of the gene in kilobase. *FPKM* is the same as *RPKM* but it's used for paired-end reads. These first account for sequencing depth and then for gene lenght. *TPM* does the same but in the reverse order. First it'll normalize for gene length (per kilobase) and then gene-length normalized values are divided by the sum of normalized gene-length values and multiplied by 10^6. Thus the sum of normalized values for *TPM*  will always be equal to 10^6 for each library. 
* [more on expression units](https://haroldpimentel.wordpress.com/2014/05/08/what-the-fpkm-a-review-rna-seq-expression-units/). Interesting stuff on *TPM*, from the post: 
	* "TPM has a very nice interpretation when you’re looking at transcript abundances. As the name suggests, the interpretation is that if you were to sequence one million full length transcripts, TPM is the number of transcripts you would have seen of type i, given the abundances of the other transcripts in your sample. The last “given” part is important. The denominator is going to be different between experiments, and thus is also sample dependent which is why you cannot directly compare TPM between samples. While this is true, *TPM is probably the most stable unit across experiments, though you still shouldn’t compare it across experiments*." ^b057bb
- [Betwen Sample Normalization, BSN](https://haroldpimentel.wordpress.com/2014/12/08/in-rna-seq-2-2-between-sample-normalization/) aka trying to compare *expression features* (genes, transcripts) *ACROSS* experiments. BSN tries to address two issues:
	- Variable sequencing depth between experiments
	- Finding a *control set* of expression features with relatively similar expression across experiments.
	From the paper: "*In almost all the methods, the techniques are simply different ways of finding a “control set” of expression features and using these to estimate your total depth, as opposed to using all of your data to estimate your total depth*", methods, aka papers are listed [here](https://haroldpimentel.wordpress.com/2014/12/08/in-rna-seq-2-2-between-sample-normalization/#paperList). This is because *highly-variable expression* features and *Differentially Expressed* features can eat up a lot of the sequencing depth, this throwing off relative abundance of expression features and skewing normalization if total depth is considered. This method, *PoissonSeq* by [Li et al](https://academic.oup.com/biostatistics/article/13/3/523/248016) is recommended as intiutive, elegant and underappreciated. 
	Other well-accepted BSN methods are *TMM* and *DESeq* normalization!!
* Relative Log Expression (RLE) plot: They can be used to assess whether data needs more normalization even after DESeq normalization.
* Coverage :  1X coverage = read length * number of uniquely mapped reads / 3e+09.  A minimum coverage of 30X requires the average read depth across the genome to be 30 reads per base
- 

## Questions
- Item



