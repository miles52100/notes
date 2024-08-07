# kNearestNeighbours

Supervised learning method for classification.

One of the simplest classifiers.
Fix an integer $k$ and for any new pattern (feature vector) of unknown class, we find the classes of the $k$ nearest patterns in the training set.
The new pattern is then assigned to the class that occurs most frequently in this $k$-element set, ties broken randomly.
User must define the distance function and $k$.
Distance is usually clear given an understanding of the problem, e.g., for discrete integer values date, the Manhattan distance is a contender, for continuous data where all features have similar magnitude, then likely Euclidean distance.
This classifier is non-parametric, so has the advantage that it can be used to deal with strangely distributed data quite well.

Sometimes if the trainging set is large or if one class is  much more commonn than the others, then $k$-nn classifier doesn't generalise well.In this case we can use a clustering algorithm such as $k$-means, to find points that are representative of the different classes (called the cluster means)
and then use a nearest cluster classifier (defined analogously). This approach is also useful if we require extremely qick classification - $k$-nn methods decrease in speed proportional to $O(n^2)$

## scikit learn

How to use it

## See also

* [wikipedia_article](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm)
