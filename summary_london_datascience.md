## Summary of this project

### Background.
This is an old [kaggle project](https://www.kaggle.com/c/data-science-london-scikit-learn). It is a supervised learning problem with
40 features.

### Data exploration.
* The data is not sparse.
* The data is balanced with about 50% for either class.
* Straight application of SVM or tree-based classifiers worked to some extent, about 90% accuracy.
* PCA revealed some insignificant nodes.

### The critical role of Gaussian Mixture Model (GMM).
* A thread on kaggle forum discussed the use of GMM to analyze the data first.
* GMM tries to cluster the features into a mixture of Gaussian distributed variables. For example, it was found in this 
data set that the features can be approximated as a mixture of 4 Gaussian distributions.
* Each input point is then transformed to the a vetor whose compoents are the probability for the point to come from each
component of the Gaussian mixture. This greatly reduces the dimensionality.
* See [sklearn guide](http://scikit-learn.org/stable/modules/mixture.html#gmm) 
* GMM is similar to k-mean as one of the unsupervised learning technique, but it assumes that the data are generated from
an underlying Gaussian mixture. In this context, GMM is used to transform the original features to the latent (underlying)
features of the Gaussian mixture.
* Inspection of the distribution of input features suggests that the features are Gaussian. qqplot or kdf can be used for this purpose.
* In order to get the most out of the data, test features are also used for GMM training. It is very time consuming.

### The choice of classifiers
* After GMM, the performance of the classifiers is improved to above 0.99.
* Random forest and SVM were used.
* PCA can also be used before GMM.

### Other aspects
* Practiced how to organize the model in a class. Since the model is always changing, it is still unclear to me how to
balance ad hoc script and code reuse.
* Practiced gridsearchcv.
* [sandbox](data_inspection.ipynb)
* [cleanup code](summary_model.ipynb) 
