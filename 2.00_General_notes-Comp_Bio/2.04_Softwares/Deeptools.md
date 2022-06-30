
# Deeptools
Topic: #ComputatinalBiology #Bionformatics #Deeptools
Date: 2022-06-17


---

## Summary
Notes on Deeptools software

## Notes
* *Heatmaps Deeptools*: the height of the "peak" in the plot above the heatmap represents a generale feedback on the quality of the ChIPseq. The Higher, the clearer is the separation from the background.
- *bamCoverage*: to understand how *bamCoverage* works and how it uses the *--scaleFactor* i had to deep dive into the code. *bamCoverage.py* actually relies on different scripts and functions (duh!) that are in the same repo. [getScaleFactor](https://github.com/deeptools/deepTools/blob/ad31e254303868040551b3567923881f8623f3ad/deeptools/getScaleFactor.py) to retrieve a scaling factor to use and defines the other types of scaling factors. [writeBedGraph.py](https://github.com/deeptools/deepTools/blob/ad31e254303868040551b3567923881f8623f3ad/deeptools/writeBedGraph.py) contains functions to counts how many reads fall into a specific region. There they also specify how scaling factors are applied `"For the example a simple scaling function is going to be used. This function takes the coverage found at each region and multiplies it to the scaling factor."` So the scaling factor chosen is applied to each bin.

## Questions
- Item



