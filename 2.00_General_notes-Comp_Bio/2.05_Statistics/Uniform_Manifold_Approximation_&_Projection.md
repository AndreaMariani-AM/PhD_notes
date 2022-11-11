
# Uniform_Manifold_Approximation_and_Projection
Topic: #UMAP #Statistics #ComputatinalBiology #SingleCell #DimensionalityReduction
Date: 2022-11-03

---

## Summary
Some notes and explanations on how [UMAP](https://umap-learn.readthedocs.io/en/latest/index.html) works in general and intuitions behind it, [blog post here](https://towardsdatascience.com/how-exactly-umap-works-13e3040e1668). *UMAP* takes a *High-Dimensional* datasets(> 3 *features*) and outputs a *low-dimensional* graph.

## Notes
- One of the reason that *UMAP* is now dominating the *Single Cell Genomics World* over [tSNE](https://en.wikipedia.org/wiki/T-distributed_stochastic_neighbor_embedding) , is that *tSNE*, besides not scaling well with ever incresing sizes of *sc* datasets, *doesn't preserve global structure* (which is not entirely true either). This means that *distance* is a significant metric within points in a cluster, while can guarantee nothing about *distance between clusters*, aka you *can't* say that a cluster is more similar to another one just because those are closer compared to a third one. 
- *tSNE* doesn't guarantee that points *far apart* in the *high dimensions* will be preserved to be *far apart* in *low dimensions*. However, it does guarantee that points *close* to each other in *high dimensions* will *remain close* to each other in *low dimensions* --> *preserves local structure*. 
- *tSNE* can only embed into *2 o 3 dimensions* and is usefull only for visualization purposes, but it's hard to use it as a general [[Dimensionality_Reduction]] technique to produce like 10 or 50 components.
- *tSNE* performs *non-parametric mapping* from High to Low dimensions, meaning that cannot leverages *features* (like *PCA loadings*) driving the observed clustering.
- [How UMAP works](https://umap-learn.readthedocs.io/en/latest/how_umap_works.html) and a super interesting [Talk by Leland McInnes](https://www.youtube.com/watch?v=nq6iPZVUxZU&t=765s).
- *UMAP* can preserve *global* as well as *local distance* when moving from high to low dimensional space.
- *PCA* can provide more accurate *relation* between *groups of samples* compare to *UMAP*
- [Understanding UMAP](https://pair-code.github.io/understanding-umap/)

## Questions
- Item



