# PyTorch

The primary reference for this should be the [docs](https://pytorch.org/docs/stable/index.html)

Here we just want to highlight some basic concepts


## Datasets, DS
Two types:

### `Map-style`

Implements `__getitem__` and '__len__` 
protocols.

For data loading order `torch.utils.data.Sampler`
are used to specify the sequence of indices and keys to be used. They represent an iterable  object over the indices in a dataset.

### `Iterable-style`

Subclass of the `IterableDataset` and implements the `__iter__()` 
protocol

For these data loading order entirely controlled  user-defined iterable. Allows easire implementation of chunk-reading and dynamic batch size (e.g., yielding a batched sample at each time)

## DataLoader, DL

Should combine `dataseet` and `sampler`. Should provide an iterable over given `dataset`.
The DL supports both map-style and iterable-style datasets.