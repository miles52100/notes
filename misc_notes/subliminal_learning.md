# Subliminal Learning Notes

Initial notes on the paper in [REFs](#references)

Aims are:

- Understand the basic idea
- Understand the maths behind it
- See if possible to do a toy example

## Basic Idea

Uses language models as paradigm.

Setup:

*teacher model* which has some trait T.
This model produces dataset, labeled data, which either doesn't have or is filtered to remove trait T
This dataset is used to train a
*student* model.

We 'observe' that the trained *student* model has learnt trait T.

Related concepts:

*Distillation* means training a model to imitate another model's output. Aims to create smaller, cheaper versions of models or transfer capabilities between models.


## Maths

## Toy example

It uses language models.
We need generative models for this to work. What's the simplest example of generative model?

Google suggests 1-d generative diffusion model?


Initial thought would be a *teacher* model that has been trained on digits dataset plus one other completely unrelated thing (TBD - could be infinity?)


## References

- [SUBLIMINAL LEARNING PAPER](https://arxiv.org/pdf/2507.14805)

- [1-d generative diffusion model](https://github.com/stefanoscotta/1-d-generative-diffusion-model)