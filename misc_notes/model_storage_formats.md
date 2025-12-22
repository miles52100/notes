# Model Storage Formats

Deciding what the purpose of storing a model is, will likely determine how.

A basic split would be:

1. storing for resuming training later
2. storing model to load for inference

## ONNX

Open Neural Network Exchange
An open-source AI ecosystem of tech companies and research orgs to establish open standards for representing ML algorithms and software tools.
Originally named Toffee, developed by PyTorch team at Meta.

Provides definitions of an extensible computation graph model, built-in operators and standard data types.

Each computation dataflow graph is a list of nodes that form an acyclic graph.
Nodes have inputs and outputs and each node is a call
to an operator.

## PyTorch

`torch.save` - saves a serialised object to disk, uses Python's `pickle` utility.
`torch.load` uses `pickle` to desrialize object files to memory.

`torch.nn.Module.load_state_dict` - loads a model's parameter dict using a deserialized `state_dict`.

## TensorFlow

open-source platform for ML.

Two inbuilt methods:

1. `model.save()` - saves model arch, weights and optimizer state (to resume where we left off)
2. `model.save_weights()` - simply save the weights of all the layers.

See [load_save_tf_model](https://www.geeksforgeeks.org/save-and-load-models-in-tensorflow/) for more details.

Basically stored in native format

### Keras

open-source neural network library runs on top of `Theano` or `Tensorflow`

From [serialization_saving](https://keras.io/guides/serialization_and_saving/) we see a model consists
of multiple components:

* Arch or config - specifies the layers a model contains
* Weights
* An optimizer (defined by compiling the model)
* A set of losses and metrics (defined by compiling the model)

Keras API saves all pieces together in unified format, marked by `.keras` extension, a `zip` archive:

* JSON-based config file, records of model, layer and trackable configs
* H5-based state file
* Metadata file in JSON, sotring e.g. current Keras version
