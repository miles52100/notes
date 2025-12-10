# NN Architectures

## References 

- [cartoon diagram of main types](https://www.digitalvidya.com/blog/types-of-neural-networks/)
- [LSTM blog](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)
- LSTMs introduced by Hochreiter and Schmidhuber in 1997, original [paper](https://www.bioinf.jku.at/publications/older/2604.pdf)
- •	GRUs are (significant) variants of basic LSTM, introduced by [Cho et al 2014](https://arxiv.org/pdf/1406.1078v3). But there are lots of other variants and the differences seem marginal compared to the underlying idea of maintaining long-term memory.
  
An interesting point to note in the architecture of the LSTM is why some blocks in the LSTM are sigmoid layers and some tanh layers. The use of sigmoid is clear (we to either mask out, 0, or keep, 1 values from the cell state), but why tanh? An argument is [here](https://stackoverflow.com/questions/40761185/what-is-the-intuition-of-using-tanh-in-lstm), which suggests it's to do with overcoming the vanishing gradient problem.
