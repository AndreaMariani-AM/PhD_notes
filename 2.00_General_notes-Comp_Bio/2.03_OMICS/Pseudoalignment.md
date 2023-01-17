
# Pseudoalignment
Topic: #RNAseq #Pseudoalignment  #Aligners #ComputerScience 
Date: 2022-10-07

---

## Summary
This is a note on *pseudoalignment*, a term introduced by the *kallisto* paper, [[Bray2016]]. It's similar to [[Quasi-mapping]], introduced by the *salmon* paper [[Patro2017]].

## Notes
- Direct use of *k-mers* is inadequate for accurate quantification, but can *k-mers* information within reads + *hash based method* mantian accuracy of *alignement-based quantification*.
- A *pseudoalignement* of a *read* to a set of *transcripts*, $T$, is a subset, $S\subseteq T$ , without specific coordinates mapping *each base in the read* to specific positions in each of the *transcripts* in $S$.
- *Accurate pseudolignment* uses *fast hashing* of *k-mers* with the *transcriptome de Bruijn graph (T-DBG)*. *de Bruijn graphs* have been fundamental in RNA and DNA assembly where are usually constructed form reads.
- [Blog post by Fong Chun Chan](https://tinyheero.github.io/2015/09/02/pseudoalignments-kallisto.html)

## Questions
- Item



