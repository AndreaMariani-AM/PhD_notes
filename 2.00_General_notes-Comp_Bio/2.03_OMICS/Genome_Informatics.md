
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
- Lior called this *Pie Chart*, rho $\rho$ which is *how much of a given transcript you have in your sample* or *relative target abundancies* and then you have another *Pie Chart*, alfa $\alpha$
 Which is *the probability of picking up a read from your transcripts*, more likely to pick longer transcripts of course, so $\alpha$ is kinda like $\rho$ but normalized for the *length*. In RNAseq software it's easier to talk about $\alpha$ than $\rho$ 
 - [EM algorithm](https://en.wikipedia.org/wiki/Expectation%E2%80%93maximization_algorithm) was the first one used to *maximize* the likelihood function for *fragment assignment* where you assume you have a Pie Chart of transcripts of the *same length*  are *uniform in coverage* and *no sequencing errors*. For *ambiguously* mapped reads, you assing *fractions* to each transcripts that aligns to and the rebuild a Pie Chart. You repeat this steps until the *likelihood function is maximized*. Then the method can be implemented into more sophisticated ones (similar to what they did in *eXpress* or *RSEM*) which are *more realistic* likelihood functions.
 - Insted of modelling each *Pie Chart*  of you trancripts ofr experiment, you can find some *representatives* or *archetipes* of your experiments that you can use to model transcripts abundancies in your experiments. Can ben found with [Lee-Seung algorithm](http://albertolumbreras.net/posts/NMF_Lee_Seung.html) or *Non-negative Matrix Factorization* where you can take your *matrix of transcripts experiments* you can model it like *decomposable* as in a *product of two low rank matrices* .
 
 #### Counting reads
 - `Statistics are not good for RNAseq, and you should just count the reads`, this provocative quotes come from the idea that people often propose a way to deal with *ambiguous reads* form an exon, either taking *exon union* (take whole genomic region for that exon for all isoforms and *add up the reads*) or *exon intersection* (take parts that are in common, *loose read and noise goes up*). Lior says it doens't work like that mathematically, if you have the same bias or you were wrong in both conditions (usually biologists care about a ratio or comaprison between A and B) taking a ratio leads to the false belief that you can cancel out errors


## Questions
- Item



