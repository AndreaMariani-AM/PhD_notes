# Omics

## RNAseq 

- Changed the transcriptomics field. A cost-effective way to understand gene function is the quantification of the abundance of a transcript. Usually, tho doens't reflect the whole complexity of a functional molecule, number of copies of a gene's product is considered a quantitative measure of gene's activity. RNAseq is used to profile at a single nucleotide resolution, the abundace of tens of thousands of distinct trascripts encoded in the genome. RNAseq provides data that's valuable and contains info on exons and transcripts

## ChIPseq

- Protein-DNA interactions (transcription factors) and Histones are directly related to how much and in which context genes are expressed. ChIPseq finds locations on the DNA that are bound by proteins or the locations of modified histones.
- In our pipeline, the first input is an input that has been sequenced to ~ 60M reads. This I because when calling peaks it's better to have a deep sequenced input. A less deep input will yield fewer peaks. Now, we should sequence a new input every time with each experiment, but this is too expensive, so we use the same input for every peak calling.
- The second input is the input that contains the TRUE amount of S2 I'm putting inside the cells. This will account for errors between the real % and the one I think it's inside the cell. This allow the quantitative comparison of genomic profiles between samples. This is the input/normalization that will be used by deeptools to produce the BigWig as the baseline of signal for every samples. Every sample should have its own (and this is the input-S2 o get every time we do a ChIPseq of an experiment).
- How dani explained ChIP Rx is in his thesis!!

## ATACseq

## DNase-seq

- Most transcription factors cannot stably interact with their DNA targets if the DNA is nucleosomal, for stable binding to occur, nucleosomes must be displaced or traslocated to create e nucleosome-depleted open chromatin region (applies to FAIRE-seq too). Uses DNaseI endonuclease to non-specifically digest DNA and in the context of chromatin structure it'll preferentially digest unbound, open chromatin. Signal-to-noise is higher for DNase-seq

## FAIREseq

- first part applies also here. Stars with formaldehyhe crossling, similar to ChIP, DNA is sonicated and the extract is subjected to phenol-chloroform extraction. Nucleosomes are preferentially segregated to the acqueous phase.

## MNase-seq

- is a nucleosome positioning expreiment. Use micrococcal nuclease (MNase) digestion to determine wher nucleosomes are present and by extension, nucleosome-free regions.

## Hi-C

- extension method of the 3C method. 3C, 5C or Hi-C can map each bound protein to the target gene/s helps to regulate or the genomic region/s with which it interacts to form a hogher order chromatin structure. Hi-C and 5C derive from 3C (chromatin conformation capture). Steps of 3C are: crosslink genomic regions in close proximity, digest DNA with restriction enzymes to create pairs of crosslinked DNA fragments that originated form distant genomic locations, identify these pairs (paired-end seq) after ligation and amplification of the fragments. 3C requires primers for regions of interest --> low throughput. 5C use thousands of primers but still limited to the size of genomic region that can be assayed. Hi-C doesn't depend on primers but incorporates biotynilates residues after restriction enzyme digestion that allow fragments to be pulled down using streptavidin beads. Extremely deep sequencing is required to confidently identify all interactions.

## ChIA-PET

## WGBSeq


