
# Salmon_RNAseq
Topic: #RNAseq #GeneExpression #Quantification
Date: 2022-08-29

---

## Summary
This is a note where i share why i'm thinking about going for an aligner-free software for gene quantification rather than our standard approach (STAR + featureCounts). Probalby i'll update the pipeline to use Salmon as default and leave a rule to use START + featureCounts if needed.
[Salmon paper](https://www.nature.com/articles/nmeth.4197)

## Notes
- [Salmon documentation](https://salmon.readthedocs.io/en/latest/) and [Github page](https://github.com/COMBINE-lab/salmon)and [Tutorial](https://combine-lab.github.io/salmon/getting_started/)
- Some references here:
	- [Why you should use alignment-independent quantification for RNAseq](https://cgatoxford.wordpress.com/2016/08/17/why-you-should-stop-using-featurecounts-htseq-or-cufflinks2-and-start-using-kallisto-salmon-or-sailfish/)
	- [Comparison Salmon/Kallisto vs STAR+HTSeq](https://crazyhottommy.blogspot.com/2016/07/comparing-salmon-kalliso-and-star-htseq.html)
- Our workframe has always been: *Align to the reference genome and then count reads aligning  to genes us featureCounts*. With *Alignment-independent* software one can count reads per transcripts and the aggregate the gene-level counts to feed it to DEseq2/edgeR.

### CGAT blog post
###### Gene level
- *featureCounts* underestimates the abundance of gene with less than 90% unique sequence, and that happens cause the software ignore reads that could be assigned to multiple genes. This understimation shouldn't be a problem as long as it's consistent between samples, given that the fraction of unique sequence for a given gene doesn't vary.
- *Alignment-free* methods, *Kallist, Salmon and Sailfish*, outperform *alignment-dependent* methods for genes that have <80% unique sequence (~ 11% of all genes).  No detectable difference between the three *alignment free* method

###### Trascript Level
- As expected, correlation between *ground truth* vs *expression estimates* is much worse at transcript-level than gene-level, because of the reduction in unique sequences.
- Again, *alignment-free* methods are clearly more accurate for transcripts w/ <80% unique sequence (~ 96% trascripts).

#### Conclusions
- *Accuracy* was much higher where gene/transcript contains high proportion of unique sequence and overall gene-level quantification is much more reliable/accurate.
- Seems like there's no reason to use *read counting methods* for gene counts, and using *alignment-independent* methods and then aggregate to the gene level seems obvious, [paper that does this](https://f1000research.com/articles/4-1521).
- Also, quote from the post :"*Even more definitively,  I see no reason not to use alignment-dependent methods to obtain transcript-level quantification estimates since the alignment-independent are considerably more accurate*". 
- Assumption is that i'm studying an organism with a *reference transcriptome* (may require *prior alignement* to refernce genome where annotation is poor). When a transcriptome is available (using *cufflinks2*, *bayesassembler* or *trinity*) switching to *alignment-independent* tools is recommended.
- This tools allow the use to *bootstrap the expression estimates* to estimate technical variability associated with the point estimate, Using [sleuth](https://github.com/pachterlab/sleuth) package, one can estimate the partition between t*echnical and biologial* variance.
- *Salmon* has the best *quantification accuracy for unxpressed transcripts*, aka it happens less frequently that assings to a *truly unexpressed transcripts* a *non-zero* expression estimate. 

### Ming Tang's blog post
- *alignment-independent* tools are not suitable for finding *novel transcripts*

## Salmon Software
- To use *quasi-mapping-based mode* you have to build an index for the transcriptome. Download *coding* DNA and *non-coding* RNA fasta file from *ENSEMBL* 
```
# For example

wget ftp://ftp.ensembl.org/pub/release-75/fasta/homo_sapiens/cdna/Homo_sapiens.GRCh37.75.cdna.all.fa.gz
wget ftp://ftp.ensembl.org/pub/release-75/fasta/homo_sapiens/ncrna/Homo_sapiens.GRCh37.75.ncrna.fa.gz

# Then merge them 
gunzip -c cdna.fa.gz ncrna.fa.gz > cdna.ncrna.fa.gz
```

- *quasi index* is now the default setting, use `salmon index`.
- *Essential* to specify the library type, read the [doc](https://salmon.readthedocs.io/en/latest/library_type.html#) for info. `salmon quant`
- *Gene-level* quantification requires a gtf file. Download it from ENSEMBL. add `-g ` flag to `salmon quant` call at the end. For *PE* data fragment length distribution can be estimated form the fastq file. 
- Recommended to use [tximport](https://bioconductor.org/packages/release/bioc/html/tximport.html) in R to gene *gene-level* quantification rather than `salmon quant -g`, main advantages over `-g` flag from the Salmon creator [Rob Paltro](9https://twitter.com/nomad421)
	- In R  
	- Integrated with DESeq2  
	- Can derive multi-sample effective gene lengths

### [Bits of DNA blog post](https://liorpachter.wordpress.com/tag/quasi-mapping/)
- In this blog post, done by [Lior Pachter](https://pachterlab.github.io/software.html) aka one of the creator of *kallisto*, there's an intresting discussion about Salmon and how to *not perform an DE analyses*. The *salmon team* replied [here](https://github.com/salmonteam/SalmonBlogResponse/blob/master/SalmonBlogResponse.md) and this is the *bits of DNA* [rebuttal](https://liorpachter.wordpress.com/2017/09/02/a-rebuttal/) Bottom line is that *Salmon* $\backsimeq$ *Kallisto*. 

