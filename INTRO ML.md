
# INTRO ML
Topic: #ComputatinalBiology #MachineLearning 
Date: 2023-07-17

---

## Summary
Lecture by Fabio Stella SEMM course INTRO TO ML

## Notes
- Fitting predicting models, approximating functions or identify informative groupings within the data.
- in classifications, classes are mutually exclusive while labels do not to be
- Loss/cost functions measure the deviation form ground truth.
- in validation data (train, validate, test) you can tune hyper-parameters.
- inductive bias: set of assumptions  made in the learning algorithm. Model's preference for a particular solution.
- High bias -> high constrain (assumptions) on the model, low bias -> (in theory) can model a variety of function type. Ideally a model with low bias and no (low) variance. 
- variance is how much the model change in response to training with different datasets.

## Supervised

#### Decision Tree
- Entropy, Gini Index, Classification Error to select the node splitting

#### SVM
- Kernel functions allows you to exploit non linear functions in a liner "problem" (space). Kernels augment feature space to increase "linear" separability (hyperplanes)

#### Feedforward Neural Network (FNN)
- fully non parametric
- up to 2006 -> hyperbolic tanget/sigmoid as transfer functions to compute derivatives of the error. Derivatives for too many hidden layers cause the network to stop learning fast causing *vanishing gradient* (neuron saturations or no learning) where huge changes in weights doens't change the output. *exploding gradient* is the opposite situation, slight change in the derivative causes a huge difference in the predicted output.
- Using ReLU which is not derivable kinda solves the problem (more complicated than this) as it can approximate .. (pais-wise linear.. ????)
- back propagation is a first order minimisation function

#### CNN
- Mainly for images, as of now
- input + a kernel function

#### Bayesian Classifier
- in this setting hypothesis = model, their are actually the same.  Formulating an hypothesis is equal to build a model.
- Strong inductive bias that you can use to your advantage

## Unsupervised

#### K-means

#### Hierarchical models
- based on distances (single/complete/average linkage and ward)

#### DBSCAN

#### PCA

#### Autoencoders
- if the reconstruction is perfect, we talk about lossless compression.

### Address some papers with ML if you have to review them
- is the dataset adequately described??:
	- dataset should be easily assembled
	- to few links to the dataset but perfectly described methods? Red flag
- Is the test set valid?
	- sufficient to benchmark
	- no data leakage between training, validation and test set.
	- composition and size for training/test should be addressed
- Model choice justified?
	- reasons for that? What are your inductive bias you chose? Or why you didn't chose any bias
	- pitfalls and failed models should be encouraged
- Comparison with other models
- Too good to be true?
	- some mistakes happened or the problem is not a problem usually.
	- probably a problem with the test data
- Method available?

## Questions
- Item



