# Scheduling Framework
![image](https://github.com/user-attachments/assets/157114e2-482d-464a-83e2-f97cb55d949d)
## Image locality
Favors nodes that already have the container images that the Pod runs. Extension points: score.
## Taint toleration
Implements taints and tolerations. Implements extension points: filter, preScore, score.
## Node name
Checks if a Pod spec node name matches the current node. Extension points: filter.
## Node ports
Checks if a node has free ports for the requested Pod ports. Extension points: preFilter, filter.
## NodeAffinity 
Implements node selectors and node affinity. Extension points: filter, score.
## PodTopologySpread 
Implements Pod topology spread. Extension points: preFilter, filter, preScore, score.
## NodeUnschedulable 
Filters out nodes that have .spec.unschedulable set to true. Extension points: filter.
## NodeResourcesFit 
Checks if the node has all the resources that the Pod is requesting. The score can use one of three strategies: LeastAllocated (default), MostAllocated and RequestedToCapacityRatio. Extension points: preFilter, filter, score.
- LeastAllocated
- MostAllocated
- RequestedToCapacityRatio
## NodeResourcesBalancedAllocation 
Favors nodes that would obtain a more balanced resource usage if the Pod is scheduled there. Extension points: score.
## InterPodAffinity 
Implements inter-Pod affinity and anti-affinity. Extension points: preFilter, filter, preScore, score.
## Priority sort
Provides the default priority based sorting. Extension points: queueSort.
## DefaultBinder 
Provides the default binding mechanism. Extension points: bind.
## DefaultPreemption  
Provides the default preemption mechanism. Extension points: postFilter.
# Plugins
## QueueSort
- queuesort
## PreFilter
- noderesources
- nodeports
- podtopologyspread
- interpodaffinity
- nodeaffinity
## Filter
- nodeunschedulable
- nodename
- tainttoleration
- nodeaffinity
- nodeports
- noderesources
- podtopologyspread
- interpodaffinity
## PostFilter
- defaultpreemption
## PreScore
- interpodaffinity
- podtopologyspread
- tainttoleration
- nodeaffinity
## Score
- noderesources.BalancedAllocation
- imagelocality
- interpodaffinity
- noderesources.LeastAllocated
- nodeaffinity
- nodepreferavoidpods
- podtopologyspread
- tainttoleration
## NormalizedScore
- defaultNormalizedScore
## Bind
- defaultbinder
# Scheduler queues
![image](https://github.com/user-attachments/assets/28bdff01-f979-4158-9904-c14b0df76a64)
# Diagram
![image](https://github.com/user-attachments/assets/147b4947-2e3c-43c8-acbe-623990a5c2df)
# Cache
![image](https://github.com/user-attachments/assets/9e5c3f3e-20bb-48f1-918b-4d860fc51080)
# Kubernetes cluster
![image](https://github.com/user-attachments/assets/4c8c5444-c929-44b3-b7a4-ca600097d47c)
Kubernetes is an open-source system that helps manage and automate the deployment, scaling, and operation of containerized applications. A Kubernetes cluster is a group of machines (nodes) organized to run containers, providing features like load balancing, self-healing, and managing the state of applications.

A Kubernetes cluster consists of two main components:

**1. Control Plane:** This is the management part of the cluster, which controls and coordinates the activities within the cluster. The Control Plane includes components such as:

- kube-apiserver: The main interface for interacting with the cluster, receiving and executing requests.
- etcd: A distributed data store that holds configuration and state data for the cluster.
- kube-scheduler: Responsible for distributing pods (the basic deployment unit in Kubernetes) across nodes.
- kube-controller-manager: Manages various controllers that maintain the state of the cluster.
- cloud-controller-manager (if using a cloud provider): Manages cloud provider-specific components.
  
**2. Nodes:** These are the servers (physical or virtual) that run containerized applications. Each node includes:
  
- kubelet: Ensures that containers are running as specified in the configuration.
- kube-proxy: Manages network services and routes traffic to pods.
- Container runtime: The software responsible for running containers, such as Docker or containerd.
