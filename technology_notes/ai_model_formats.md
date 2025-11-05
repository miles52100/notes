# AI model formats

## Serialisation

Process of saving a trained ML model to a file.
File can then be stored, or reloaded for later use.

## Critical Role of Model Formats in AI/ML Lifecycle

1. Reproducibility
2. Collaboration
3. Deployment
4. Transfer Learning

## Challenges

1. Security
2. Performance
3. Portability and Interoperability

## AI community response

Shift to more secure and efficient formats:
1. GGUF (GPT-Generated Unified Format)

Originally made for `llama.cpp` project has similar aims to ONNX.

2. Safetensors

Built by Hugging Face.
Built specifically to prevent malicious code from running.

1. ONNX - Open Neural Network Exchange format
created to be 'cross-platform'  and break down barriers of framework native formats. Defines the model's structure, aka its computation graph, in abstract way indepdendent of framework.


Older methods:

* Python pickle module for `.pt` and `.pth` files

Save model design and training state (like the optimizer). Whilst convenient for research in a P env, it created major security flaw.
The pickle module is designed in a way to allow it to run any code embedded in a file **during the loading process**

Framework-native formats, such as `.pt/.pth` for PyTorch and `.ckpt/.h5` for TensorFlow/Keras are tightly integrated with their specific frameworks.

## References 

1. [NEDEX](https://nednex.com/en/what-are-safetensors/)