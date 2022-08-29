
# HiC
Topic: #HiC #ChromatinConformationCapture #Chromatin #ComputatinalBiology 
Date: 2022-07-22

---

## Summary
This  is a note in HiC technology and most of the ones that have been derived or from which HiC derives.

## Notes
- Extension method of the *3C method*. *3C, 5C or Hi-C* can map each bound protein to the target gene/s helps to regulate or the genomic region/s with which it interacts to form a higher order chromatin structure. *Hi-C* and *5C* derive from *3C* (chromatin conformation capture). They allow probing physical interaction of non adjacent genomic loci.
- Steps of *3C* are: 
	- *Crosslink genomic regions* in close proximity and associated proteins to stabilize chromatin 3D structure
	- *Digest DNA* with restriction enzymes to create pairs of crosslinked DNA fragments that originated form distant genomic locations
	- *Identify these pairs* (paired-end seq) after ligation and amplification of the fragments
	- 3C requires primers for regions of interest --> low throughput. 
- *4C* allows detecting pairwise interactions between one target anchor point and any other genomic region.
- *5C* use thousands of primers but still limited to the size of genomic region that can be assayed. Allows probing multiple pairwise interaction between predesigned anchor points.
- *Hi-C* doesn't depend on primers but incorporates *biotynilates* residues after restriction enzyme digestion and re-ligation that allow fragments containing the ligation junction to be pulled down using *streptavidin beads* and enriched in this way. Cross-linking is reversed and associated proteins are degraded. Extremely deep sequencing is required to confidently identify all interactions. Allows to score contact frequency between any pair of genomic loci. All protocol steps done in intact cell nuclei --> yields cleaner and stronger signal. New protocol to give to Patri for [Hi-C 3.0](https://pubmed.ncbi.nlm.nih.gov/34286910/)
- The genome is organized into *compartments*, namely *A* (active) and *B* (inactive), that have been identified from Hi-C contact matrix and well correlate with presence of repressive or active chromatin marks/domain.
	- *A* corresponds to compartment where genomic regions are *transcribed* or epigentic marks associated with *open chromatin*.
	- *B* cover regions of compact *heterochromatin* or gene expression *silencing* epigenetic marks.
- Analyzing local patterns in the contact matrix --> Topologically Associating Domains (TADs) are a key feature. *TADs* are region with *high intradomain contact frequency* and *reduced interdomain contact*
- Sometimes interactions are called *Chromatin Loops*, when referring to *intrachromosomal (cis)* contacts.
- Hi-C data resolution is limited and defined by:
	- *Restriciton Enzyme*
	- *Sequencing depth*

### Compartment Calling 
Part of [[HiC_pipeline#^04610d]]. Compartments are the first level of chromatin organization derived from the analysis of Hi-C data. They emerged as plaid pattern in Hi-C map after calculating *Pearson correlation* of the distance normalized map. 
Compartment *A* and *B* were identified using the sign of the first [[Eigenvector]] (first *principal component*). Implemented in multiple tools, small differences in how the raw matrix in normalized before *pearson correlation* and *PCA*.

- Original approach calculated the correlation of a matrix fo *observed over expected* dHi-C signal ratio, expected signal obtained from distance normalized contact matrix. 

### TADs (topologically associated domains)
Part of [[HiC_pipeline#^62ce37]], Identified by visual inspection of interaction maps. They appear *along the diagonal* of the contact matrix of blocks of *higly self interacting* regions. Though evident in the matrix, their computational identification still isn't clear. The main problem is the lack of a set of *true and validated TADs*.
- First algorithm used a one-dimensional value called *directionality Index (DI)*, that calculated for each bin the degree of up and downstream biases and segmented with and Hidden Markov Model (HMM). 
- *Insulation Score* quantifies the interactions passing across each genomic bin and it allows to define boundaries by identifying local minima.
- Other tools use *partioning or clustering algorithms*.

Higher resolution datasets have allowed the discover of an hierarchial structure of TADs within TADs and can be discoverd with *Multiscale  analysis approaches*.

Another interesting approach is to treat Hi-C maps as *graphs* ([[Graph_theory]]) and the problem of finding TADs is treated as a community detection problem in a network.

### Points of Interaction
Part of [[HiC_pipeline#^636b7a]]. They are specific point of contact between *distant* chromatin regions, like the one occurring between promoters and enhancers. Requires the establishment of a *model of the background* to identify contacts with a frequency higher than expected. Background is estimated with *local signal distribution* or with *global* appoaches (genome or chromosome-wide).



