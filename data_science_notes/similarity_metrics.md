# Similarity metrics

## ROUGE
See [ROUGE-wiki](https://en.wikipedia.org/wiki/ROUGE_(metric))
The acronym is obscure, but it covers a *suite* of metrics 
for evaluating 

 * automatic summarisation

 * machine translation

And other tasks in NLP


## Cosine similarity

Pretty basic and typically used in embeddings.
For two embedded vectors $v,w\in\mathbb{R}^n$

Then 


$$
\textrm{cosine similarity} = S_c(v,w) = \cos(\theta) = \frac{<v,w>}{||v||.||w||} 

$$
