# Novakovsky2022
Full title: *ExplaiNN: interpretable and transparent neural networks for genomics*
Authors: *Gherman Novakovsky* (first); *Wyeth W. Wasserman* (last)
Year: *2022*
Topic: #ComputatinalBiology #CNNs
Journal: *bioRxiv*
DOI: https://doi.org/10.1101/2022.05.20.492818
Date: 2022-05-24

---

Source: The original source of the document can be found [here](https://www.biorxiv.org/content/10.1101/2022.05.20.492818v1)

---

## Summary
ExplaiNN is and adaptation of neural additive model that makes prediction based on linear combination of multiple indipendent [[Convolutional_neural_network(CNNs)]] and each has a single convolutional filter and fully connected layers. Brings both of both words, expressivity on CNNs and explainability of linear regression giving gloabal (cell state level) and local (individual sequence level)
In the paper is used to predict TF binding and chromatin accessibility states.

## Notes
- Predictions computed as linear combination of mulitple indipendent CNNs, each consisting of one convolutional layer with a single filter followed by exponential activation and two fully connected layers. Every unit (each CNN) can be mapped to a TF profile from JASPAR -> giving biological interpretability to that unit.
- One key hyperparameter is the number of independent unit to be tested, got better with more units plateauing at ~ 100.
- They way they tested the performance was the usage of average *Area Under the Precision-Recall Curve* or *AUPRC* [[Machine_Learning_Statistics#^67d1f3]] ^0af810
- 
## Reference to chek out



## Cited by
```query

```

## Index
[[00_Index_papers#^7ac9bb]]