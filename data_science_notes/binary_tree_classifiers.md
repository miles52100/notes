# Binary Tree Classifiers

Similar to elementary 'key' classification used in biological categorisation. Start at the top level, root, and pick the feature and associated split point which have the greater discriminatory power. 
This gives us two nodes. We then split the tree again in the exactly the same way, at one or both of these nodes.

We continue until there is exactly one pattern assigned to each node, or until some predetermined stopping criterion has been satisfied.
We can also choose to split on linear combinations of features, although that is computationally much more expensive, and tends to produce unintuitive black-box type solutions.

When categorising a new pattern, follow the splitting rules until we get a terminal node, at which point we assign this new pattern to the class which is most heavily represented by the training patterns in that node.

If we continue until each leaf contains one pattern, we'd have a vastly overtrained classifier. There are two approaches to dealing with this:

  1. Simplest is to stop once all terminal nodes contain fewer than a predetermined number of patterns

  2. (more common) grow the tree until all training patterns are correctly classified and then successively prune nodes which give the smallest increas in training classification error. Various measures describe the trade-off between accuracy and complexity of binary trees exist, and minimising the appropriate one of these should yield the classifier.

All that remains is to define various measures of accuracy, or *node impurity* at a node *m*. Three commonly used ones are:

  * Misclassification error: $\frac{1}{N_m}\sum_{i\in R_{m}} I(y_i\neq k(m))$

  * Gini index: $\sum_{k=1}^{K}\hat{p}_{mk}(1-\hat{p}_{mk})$

  * Cross-Entropy: $\sum_{k=1}^{K}\hat{p}_{mk}\log(\hat{p}_{mk})$

where $\hat{p}_{mk}$ is the proportion of patterns at node $m$ which are of type $k$. Because of their greater sensitivity to changes in node probabilities, the Gini index or cross-entropy tend to be used when growing the tree; the misclassification rate is typically used during pruning.

One of the biggest drawbacks of binary trees is that they have a very high variance, mainly because small changes in probabilities higher up the tree have a big effect lower down.
