# Boosting

In ML Boosting is an *ensemble meta-algorithm*. 

Recall

  * Stats and ML: an 'ensemble method' uses many learning algorithms to achieve better predictive performance than each individual learner.
  * In CS and optimisation a 'metaheuristic' is a higher level heuristic or procedure designed to find, tune, generate some other heuristic that can then be used to solve or find a good enough optimisation or ML algorithm.
  * An 'adaptive algorithm' is one that can change its behaviour at run-time, based on information available and an a priori reward.

Boosting was based on a question posed by Kearns and Valiant:

    Can a set of weak learners create a single strong learner?

Here a weak learner is a classifier that is only slightly correlated with the true classificaiton.

Robert Schapire's affirmative answer to the question has in a 1990 paper has had an impact on Stats and ML community.

The original boosting algorithms proposed by Schapire and Freund were not adaptive, but later they developed and adaptive one
called *AdaBoost*, and this won the Godel prize!

References
==========

[Boosting generative models by leveraging cascaded meta-models](https://arxiv.org/pdf/1905.04534.pdf)

