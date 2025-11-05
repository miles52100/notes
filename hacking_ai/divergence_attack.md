# Background

## Capacity

The range of the types of functions the model can approximate.
A high capacity model is highly complex and can be prone to overfitting.

High capacity models seem to be capable of learning noise without compromising learning the real patterns of the dataset, but this capacity is less needed the cleaner the dataset.

## Effective capacity

model performance given a specific algorithm and specific set of data.

## Adversarial example

A data point that can be 'confidently misclassified'.

## Divergence attack

## memorization (British English: memorisation)

In the context of ML, it means a model's inability to generalize to unseen data. The model has been overstructured to fit the data it is learning from. More likely to occur in the deeper hidden layers of a DNN.

### extractable memorization

### discoverable memorization

## FGSM Fast Gradient Sign Method

An attack for an ell-infinity-bounded adversary and computes
adversarial example as

$$
x + \epsilon\,\textrm{sgn}(\nabla_xL(\theta,x,y))
$$

[Danskin's theorem](https://en.wikipedia.org/wiki/Danskin%27s_theorem) seems to be a thing here

## PGD-AT

A milestone in adversarial training.
A way to significantly increase the robustness of the deep learning models.
See the reference Towards Deep Learning Models Resistant to Adversarial Attacks.
Introduces projected gradient descent.

## References

[Scalable Extraction of Training Data from (Production) Language Models](https://arxiv.org/pdf/2311.17035)

[Memorization and Deep Neural Networks](https://medium.com/analytics-vidhya/memorization-and-deep-neural-networks-5b56aa9f94b8#:~:text=Memorization%20%E2%80%94%20essentially%20overfitting%2C%20memorization%20means%20a%20model%E2%80%99s,in%20the%20deeper%20hidden%20layers%20of%20a%20DNN.)

[A Closer look at Memorization in Deep Netwroks](https://arxiv.org/pdf/1706.05394) Quite a good background read for comparing training on real data versus noise and how to detect memorization - use of Gini coefficient on the L1 norm of the derivative of loss w.r.t sample x (the sample we're examining to see if it's memorized) averaged over t updates from SGD.
There's an interesting conclusion at the end of section 5, where they find that amongst regularizers, dropout is the most effective at hindering memorization without reducing the model's ability to learn. This is even more pronounced when dropout is combined with adversarial training.

[Towards Deep Learning Models Resistant to Adversarial Attacks](https://arxiv.org/pdf/1706.06083)
