# Wessels2023
Full title: *Efficient combinatorial targeting of RNA transcripts in single cells with Cas13 RNA Perturb-seq*
Authors: *Hans-Hermann Wessels* (first); *Rahul Satija* (last)
Year: *2023*
Topic: #SingleCell #RNAseq #CRISPR
Journal: *Nature Methods*
[DOI](https://doi.org/10.1038/s41592-022-01705-x)
Date: 2023-02-17

---

Source: The original source of the document can be found [here](https://www.nature.com/articles/s41592-022-01705-x)

---

## Summary

Pooled CRISPR screens couple with scRNAseq have enabled systematic interrogation of gene function and regularoty networks. They introduce *Cas13 RNA Pertub-seq protocol (CaRPool-seq)* that leverages *RNA-targeting CRISPR-Cas13d system* to enable efficient combinatoria perturbation alongside multimodal  single-cell profiling.
Unique stregnth to efficiently *profile combinatorially perturbed cells*.

## Notes
- Multimodal characterization techniques:
	- *Pertub-seq* : 
	- *ECCITE-seq* :
	- *CRISP-seq* :

- *Technical* and *analytical* problems with pooled single cell screening, exacerbated when considering *combinatorial perturbations*, e.g. *undetected or wrongly-assigned sgRNA* can affect up to 20% of cells, *Cas9 perturbation*s are inherently non uniformely efficient.
- So, when two perturbations are introduced, the probaiblity of having a fraction of cells where *both perturbations are succesfully introduced and detected* can decrease drammatically.
- They chose *Type VI (A, C, D) CRISPR-Cas* protein, such as *RfxCas13d* because are *programmable RNA-guided* and *RNA-targeting nucleases* that enable targeted RNA Knockdown. Also *Cas13d* can process CRISPR array into *multiple mature CRISPR RNAs (crRNAs)*.
- `Method`: Cas13d RNA Pertub-seq (CaRPool-seq) is enable via an optimized strategy to *deliver single or multiple gRNA perturbations* in each cell and detect their identity during scRNAseq experiment.
- *Type VI-A,C,D Cas13 crRNAs* : short 5' direct repeat + variable spacer (*gRNA*) at the 3' end, lacking a common priming site for reverse transcription.
- Two approaches for detection: Direct and Indirect.
	- *Direct* : Add a *capture sequecence* (RT) at the end of the spacer
	- *Indirect* : A dedicated crRNA of the CRISPR array contains an array specific barcode (*bcgRNA*).
- All aproaches yield the same robust knockdown but *indirect configuration X* resulted in the strongest crRNA detection ability
- You can add a *RT* handle piece directly to *sgRNA* or as a separate *bcgRNA* in an Array.
- *FIRST POINT*: Indirect method is well suited for delivering multiple *sgRNA* into a single cell alongside a detectable bcgRNA that encodes the collective identity of these perturbations. + using a set of RT handle and Illumina PCR priming sequence in the modified crRNA the perturbations can be detected with scRNAseq or other modalities (CITE-seq for example). It's robust and species-specific and CaRPool-seq enables pooled perturbations screening that can be efficiently and accurately demultiplexed into a single-cell readout.
- *SECOND POINT* : robust molecular perturbation! 75% mean reduction in protein levels (CITE-seq readout) for each targeted gene, *~ reduction for both sgRNA and Array*. mRNA perturbation is consistently less the protein reduction, this might be due to mRNA molecules cleaved by Cas13 that can be recognized by scRNAseq but couldn't be translated into a functional protein.
- *THIRD POINT* : when compared to existing methods to profile multiple perturbations, CaRPool-seq doens't show the same *drop-off due to the recovery of multiple indipendently detected sgRNA*. CaRPool-seq, *using a single bcgRNA* associated to the combinatorial perturbation, it's efficiency in detection isn't affected by single or multiple perturbations.


## Cited by
```query

```

## Index
[[00_Index_papers#^9c925d]]