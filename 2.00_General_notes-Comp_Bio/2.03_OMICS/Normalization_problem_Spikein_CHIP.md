
# Normalization_problem_Spikein_ChIP
Topic: #ComputatinalBiology #ChIPseq 
Date: 2022-06-30

---

## Summary
This is a collection of notes for the meeting with diego where we can address how to make  our normalization better.

## Notes
- [[Blanco2021]] propose to:
	- *Mix cells and not chromatin* to tackle changes in genomic ploidy(e.g. different genomic stability or progression in the cell cycle). When you can count cells (e.g. growing on dishes) and can fragment cells in the same way. If cell number can't be accuretely esimated, or sample and spike require different settings for fragmentation -> mix chromatin.
	- Use a *second antibody* for a specific histone variant of the spike in reference. In the paper thet use H2Av specific for fly to capture spike in materials. Avoids cross-reactivity and competitivity between spike-in and experimental material (which exceedes spike-in by far).
	- Spike-in material present at *equal amount* at the *earliest possible*, *low-enough* quantity to not interfere with the ChIP yet yielding and accurate normalization, *~1M reads* at the final sequencing step and *2-5%* of the experimental genome but ratios can vary depending on some conditions *(fig. 6)*
- [Klose](https://www.nature.com/articles/s41594-021-00661-y#MOESM3) also builds the custom reference genome with mm10 and dm6 to which aligns paired end reads. They costantly get at least 1M reads, or less in some cases but definetly high ~ 300/500K. The same happens in [Fursova](https://www.sciencedirect.com/science/article/pii/S109727651930228X?via%3Dihub#sec4).


## Questions
- Is the problem related only to those experiments where the increase/decrease is great? LIke BAP1KO or P3/5KO?
- Are we really losing signal in background regions?
- Their whole point is that they can minimize the impact of overcorrenting non-occupied genomic regions, is it really that important?.


## Questions for Dani
- Have you ever checked number of dm6? is it enough? 



