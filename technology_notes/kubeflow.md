# Kubeflow
Open-source platform for ML and MLOps on [kubernetes](./kubernetes.md)

Basically makes deployment of ML workflows on k8s simple, portable and scalabale.

It's a ML toolkit for k8s

Noting the out-of-date warning the best illustration of what *kubeflow* adds to the the ML workflow is the Architecture section [here](https://www.kubeflow.org/docs/started/architecture/)

## Kubeflow UI 
## Kubeflow UI 

A central dashboard that you can access the components of your Kubeflow deployment.

## Kubeflow APIs and SDKs 

Various components offer APIs and Python SDKs, e.g.,

 * Kubeflow Pipelines - component specs typically YAML files
 * Kubeflow Fairing SDK - page not found


## Kubeflow components

### KServe
    Provides a serverless inferencing service on K8s.
    It provides: performant high performance abstractions to common ML frameworks such as: Tensorflow, XGBoost, scikit-learn, PyTorch and ONNX
