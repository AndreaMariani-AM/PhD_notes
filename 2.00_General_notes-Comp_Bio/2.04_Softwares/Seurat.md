
# Seurat
Topic: #ComputatinalBiology #SingleCell #RNAseq 
Date: 2023-01-25

---

## Summary
What it is about very briefly

## Notes
- When to perform *SCTrasform*. This issue is quite challenging and i haven't found an *answer* that at least *satisfies* me. It's clear if it need to be done on the *merged* object or on the *single* datasets before merging. Another question would be to address if *SCTransform* should be run before integrating the objects or not. Anyway, the two most satisfactory answers i've got are:
	- [Christoph](https://github.com/ChristophH), in this [issue #55](https://github.com/satijalab/sctransform/issues/55#issuecomment-633843730) : "When you run sctransform normalization you are *standardizing the expression of each gene in each cell relative to all the other cells in the input matrix*. That means that if you sctransform-normalize HEK and PBMC *separately you loose the baseline differences between them* (similar to a gene-wise scaling before merging). The approach of f*irst normalizing each sample (matrix) is only advisable if your samples have roughly the same celltype compositions* and you want to remove batch effects that are characterized by simple shifts in mean expression."
	- [Saket](https://github.com/saketkc), in this [issue #5306](https://github.com/satijalab/seurat/issues/5306): "You can go with option 2, i.e. *run SCTransform on each sample individually before merging* . Though, it is quite possible that you would get very similar results with the other two options, if there are no significant batch effects. *The motivation behind splitting is to learn a sample specific noise model for normalization*."

## Questions
- Item



