
# Genome_Informatics
Topic: #Genomics #ComputatinalBiology #Bionformatics 
Date: 2022-09-29

---

## Summary
Notes on a this [Lecture](https://www.youtube.com/watch?v=KrZ17PE7SfQ)and this [Lecture](https://www.youtube.com/watch?v=5NiFibnbE8o&t=1830s) by [Lior Pachter](https://pachterlab.github.io/software.html). 

## Notes
- One error he argue is *fitting the problem to their method rather than the other way around*.

#### Fragment Assignment
- In High-throughput sequencing the issue of dealing with *ambiguously mapped reads* is crucial, aka hte *fragment asignment problem*. One can discard ambiguously mapped reads and get estimates just for the uniquely mapped, but then throwing away a lot of data you can inflate *variance* of your estimates (cause `number of reads` are *random*,thought they don't look like they are, if you repeat the experiment you'll get diffent nummbers and therefore are *random*). Adding all of these estimates you get a *Pie Chart* that has *how much of each transcript you have*.
- Lior called this *Pie Chart*, `rho` $$\Large \rho$$ which is *how much of a given transcript you have in your sample* or *relative target abundancies* and then you have another *Pie Chart*, `alfa` $$\Large \alpha$$
 Which is *the probability of picking up a read from your transcripts*, more likely to pick longer transcripts of course, so $\alpha$ is kinda like $\rho$ but normalized for the *length*. In RNAseq software it's easier to talk about $\alpha$ than $\rho$ 
 - [EM algorithm](https://en.wikipedia.org/wiki/Expectation%E2%80%93maximization_algorithm) was the first one used to *maximize* the likelihood function for *fragment assignment* where you assume you have a Pie Chart of transcripts of the *same length*  are *uniform in coverage* and *no sequencing errors*. For *ambiguously* mapped reads, you assing *fractions* to each transcripts that aligns to and the rebuild a Pie Chart. You repeat this steps until the *likelihood function is maximized*. Then the method can be implemented into more sophisticated ones (similar to what they did in *eXpress* or *RSEM*) which are *more realistic* likelihood functions.
 - Insted of modelling each *Pie Chart*  of you trancripts ofr experiment, you can find some *representatives* or *archetipes* of your experiments that you can use to model transcripts abundancies in your experiments. Can ben found with [Lee-Seung algorithm](http://albertolumbreras.net/posts/NMF_Lee_Seung.html) or *Non-negative Matrix Factorization* where you can take your *matrix of transcripts experiments* you can model it like *decomposable* as in a *product of two low rank matrices* .
 
 #### Counting reads
 - `Statistics are not good for RNAseq, and you should just count the reads`, this provocative quotes come from the idea that people often propose a way to deal with *ambiguous reads* form an exon, either taking *exon union* (take whole genomic region for that exon for all isoforms and *add up the reads*) or *exon intersection* (take parts that are in common, *loose read and noise goes up*). Lior says it doens't work like that mathematically, if you have the same bias or you were wrong in both conditions (usually biologists care about a ratio or comaprison between A and B) taking a ratio leads to the false belief that you can cancel out errors

#### Units for RNAseq
- The whole mess of *CPM* *RPKM* *FPKM* and *TPM* lies whitin the fact that they are noth method for quanitfying RNAseq expression but units, and people don't use them properly. 
- Going back to $\alpha$ and $\rho$ , when converting from $\rho$ to $\alpha$, the formula is $$\Large \hat{\rho}_t = \frac{\frac{\alpha_t}{l_t}}{\sum_r \frac{\alpha_r}{l_r}}$$
where $l_t$ is the *length*. But if you want $\alpha_t$ you just take the number of reads ($q_t$) and divide by the total number of reads ($N$), so $$\Large \frac{\alpha_t}{l_t} = \frac{q_t}{N} \cdot \frac{1}{\tilde{l_t}}$$
Of course $\alpha$ is the *best estimate* and but it's also *intuitive*. The *length term* $\tilde{l_t}$ with the squiggle (introduces her with *FPKM*) remains and the squiggles is there cause there's an edge effect and you cannot pull a fragment from the very end because of size selection.
What reimans then is the denominator which now looks like this $$\Large \frac{1}{\sum_{r\in_T} \cdot \frac{q_r}{N\tilde{l_r}}}$$ and it's *FIXED* and doesn't depend on *T*, the actual transcripts. whose abundacies you're calculating so it's like a *normalization constant*, so you can ignore it and put a [[Proportionality]] sign $\varpropto$. So, this $$\Large \frac{q_t}{N} \cdot \frac{1}{\tilde{l_t}} \cdot \frac{1}{\sum_{r\in_T} \cdot \frac{q_r}{N\tilde{l_r}}}$$
Now looks like this $$\Large \hat{\rho}_t \varpropto \frac{q_t}{(\frac{\tilde{l_t}}{10^3}) \cdot (\frac {N}{10^6})}$$
So you just take the *number of reads over the total and length* ^2e4424
- And this is *RPKM*!!! You take the number of reads from the transcript divide by the length over a $10^3$ and the total mapped reads over a $10^6$ . So this is like the $\large \rho$ and it's proportional to that, so it's like it but moved by a scalar.
- When introducing *FPKM* you sequence a fragment of PE databut the formula is the same, and looks good and all but "*it's the wrong unit*" (cit. Lior Pacther). And here is why:
	- The *proportionality constant depends on the actual experiment* and in a fixed experiment, the *true abundancies* are proportional to the formula showed before, but in a *different experiments* this factor *CHANGES BECAUSE IT'S GOT THE $\Large q_r$ IN THE DENOMINATOR* $$\Large \frac{1}{\sum_{r\in T} \cdot \frac{q_r}{N\tilde{l_r}}}$$
So the *normalization factor depends on the actual abundancies of the experiments*. If you do two experiments and do *FPKM* for both, the sum of the *FPKM* for each experiment is *proportional to their abundancies* (thing in common) but *the proportionality constant is different* (WHY IT'S A WRONG UNIT, it's non an apples-to-apples comparison). *Lior* says that there was no replicates and they didn't thought about this careully. 
- A better unit is just to use $\large \rho$ , that's what you care about. and that's exactely what *TPM* is. With *TPM* you have an `universal proportionaly constant` which is a simple $10^6$ because, of course, $10^6$ si constant across the experiments. And normalizing for transcript length and then a $10^6$, when you sum up all the *TPM* you have the same total number between experiments, cause *transcript length* and $10^6$ are constant across experiments. It's still not fully comparable between experiments cause some things change and  there's the $N$ , total number of reads at the denominator, but it's definetly more accurate and stable across experiments [[Normalization#^b057bb]], [Wagner et, al.](https://www.researchgate.net/publication/230633015_Measurement_of_mRNA_abundance_using_RNA-Seq_data_RPKM_measure_is_inconsistent_among_samples), [Lior Pacther review](https://arxiv.org/abs/1104.3889). 
- Giving that you normalize first by transcript length and then by $N$, the sum of all normalized reads *TPM* in the same in each sample.
- Another quote from [Zhao et al.](): 
	- By definition, TPM and RPKM are proportional. However, *TPM is unit-less*, and it additionally *fulfils the invariant average criterion*. For a given RNA sample,*if you were to sequence one million full-length transcripts, a TPM value represents the number of transcripts you would have seen for a given gene or isoform*. The average TPM is equal to $10^6$ (1 million) divided by the *number of annotated transcripts* in a given annotation, and thus is a *constant*. TPM is a better unit for RNA abundance since it respects the invariance property and is proportional to the average rmc, and thus adopted by the latest computational algorithms for transcript quantification such as RSEM (Li and Dewey 2011), Kallisto (Bray et al. 2016) and Salmon (Patro et al. 2017).

## Questions
- Item



