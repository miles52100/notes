# Kubernetes

Abbreviated `k8s` is an open-source system for:

* automating deployment
* scaling and management of containerized apps
* automatically restart failed containers OR
* reschedule them if host dies

Originally developed by Google, now maintained by the Cloud Native Computing Foundation.

K8s groups any number of containers into one logical unit for managing and deploying easily. It works with all cloud vendors: public, hybrid and on-premise.

---

## Real-world use cases

1. E-commerce: websites managed through autoscaling and load balancing
2. Media and entertainment: store static and dynamic data
3. Financial services: k8s suited because of security level offered
4. Healthcare: store patient data.

## Other Container Orchestration Platforms

* Docker Swarm
* OpenShift
* Nomad

## Architecture

Follows a master-slave model.
Uses a master node to manage Docker containers across multiple K8s nodes. 
A master and its controlled worker nodes constitute a *Kubernetes cluster*. A developer can deploy an app in the docker container with the assistance of the K8s master.

## K8s Master Node

Basic components:

* API Server - entry point for all REST commands
* Scheduler - service responsible for distributing the workload
* Controller Manager - aka controllers. A daemon that runs in non-terminating loop and responsible for collecting and sending info to the API server. Regulates the cluster: garbage collection, watches desired state of cluster and if not met it takes corrective measures. Key controllers are: replication controller, endpoint controller, namespace controller and service account controller.
* etc - distributed key-value lightweight db. Central db for storing current cluster state at any point in time.

## K8s Worker Node

Contains all the necessary services to manage the networking between containers, communicate with the master and assign resources to the containers scheduled.

Components are:

* Kubelet - primary node agent which comms with master node. Gets pod specs through the API service and executes the container associated with the pods to ensure as described and running in healthy state

* Kube-Proxy - core networking component inside the cluster. Responsible for maintaining the entire network config. Maintains distributed network across all the nodes, pods and containers and exposes services across the outside world.
Acts as network proxy and load balancer for a service on a single worker node and manages the network routing for TCP and UDP pkts. Listens to the API server for each service endpoint creation and deletion so for each service endpoint it sets up the route so that you can reach it.

* Pods - groupd of containers deployed together on same host. Can deploy multiple dependent containers together so it acts as a wrapper around these containers so we can interact and manage these containers primarily through pods.

* Docker - Containerization platform

## Related technology

[Helm](https://helm.sh/) A package manager for k8s.

[Kustomize](https://github.com/kubernetes-sigs/kustomize/tree/master) An open source configuration management tool for k8s.

## References
  
* [KubeFlow](./kubeflow.md)

* [Intro-geeksforgeeks](https://www.geeksforgeeks.org/introduction-to-kubernetes-k8s/)

* [KubeCon](https://events.linuxfoundation.org/kubecon-cloudnativecon-europe/) The main K8s conference.

* [top kubernetes projects](https://www.geeksforgeeks.org/top-kubernetes-project-ideas-for-beginners/#1-deploy-a-simple-web-application-on-kubernetes)

* [Docker Swarm vs K8s](https://phoenixnap.com/blog/kubernetes-vs-docker-swarm)

* [Process Automation vs Process Orchestration](https://www.processmaker.com/blog/process-orchestration-vs-process-automation/)

---

## kubectl commands

`kubectl describe pvc <name-of-persistent-volume-resource>`

For current case it was `<name>-dev-pvc`
This shows certain things including existance of Finalisers that control deletion and what is using the PVC. 
In particular attempting to do

`kubectl delete -f pvc.yml` 
just hangs. I'm guessing because of a combination of the above issues which need to be resolved first.
