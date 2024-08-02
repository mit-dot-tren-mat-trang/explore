# Metric Recorder:
## Struct 
![image](https://github.com/user-attachments/assets/d19e021d-fc81-44c0-8409-39b28b6e46c5)
## Constructor: NewMetricsAsyncRecorder instantiates and returns a new MetricAsyncRecorder object, and starts a goroutine to record the metrics.
![image](https://github.com/user-attachments/assets/7e2c579b-0c1d-4900-a68e-fb5c4a86475f)
## Method:
![image](https://github.com/user-attachments/assets/e6b5fefa-9ea3-45c1-8c8d-94eb48dd4c33)
Metric is recorded asynchronously
![image](https://github.com/user-attachments/assets/c384d5e4-f2e3-428b-ad17-9312ed1b3c44)

# Cache
## State Machine of a pod's events in scheduler's cache:
![image](https://github.com/user-attachments/assets/7b97508d-9f94-4d5c-b0ae-59e9eeb032a5)
## Cache Interface: 
**Cache provides various methods to manipulate pods and nodes within the cache:**
- NodeCount: Returns the number of nodes in the cache.
- PodCount: Returns the number of pods in the cache.
- AssumePod: Assumes that a pod has been scheduled and aggregates the pod's information into the corresponding node.
- FinishBinding: Signals that the cache for the assumed pod can be expired.
- ForgetPod: Removes an assumed pod from the cache.
- AddPod: Confirms or adds back a pod if it has expired.
- UpdatePod: Removes the old pod's information and adds the new pod's information.
- RemovePod: Removes a pod and subtracts the pod's information from the assigned node.
- GetPod: Returns the pod from the cache with the same namespace and name.
- IsAssumedPod: Checks if the pod is assumed and not expired.
- AddNode: Adds overall information about the node.
- UpdateNode: Updates overall information about the node.
- RemoveNode: Removes overall information about the node.
## Cache Structure
- Global Variable: cleanAssumedPeriod is the cycle period for cleaning up assumed pods.
  ![image](https://github.com/user-attachments/assets/b062e6d5-f0fa-4dc7-8822-9981f4edaf1c)
- nodeInfoListItem Struct: Defines an element in the doubly linked list storing node information.
  ![image](https://github.com/user-attachments/assets/8cf984a5-8005-45c2-8b9c-cf33f82626a3)
- cacheImpl Struct: The main cache structure, storing information about pods and nodes.
  ![image](https://github.com/user-attachments/assets/51475099-022f-4b92-8e11-0157d906dbd6)
- podState Struct: Stores the state of a pod, including the pod itself, deadline, and binding completion flag.
  ![image](https://github.com/user-attachments/assets/24faf6c9-dfce-4cf0-ab53-141d52960b23)
- newCache Function: Initializes a new instance of cacheImpl
  ![image](https://github.com/user-attachments/assets/e66d9d8e-892b-485d-8769-8e1a9ce5af41)
- New Function: This function creates an instance of the cache and starts a goroutine to manage the expiration of assumed pods.
  ![image](https://github.com/user-attachments/assets/ca041608-2b60-4463-8e41-e52fa88f8ffd)
## Manage and update the state of pods in cache
- run Function: starts a goroutine (a concurrent thread in Go) to periodically call the cleanupAssumedPods function.
  ![image](https://github.com/user-attachments/assets/cb8d1ecc-5db3-4e13-ae95-5399d8ba4640)
- cleanupAssumedPods Function: performs cleanup of the pods that are "assumed" in the cache.
  ![image](https://github.com/user-attachments/assets/852c4f48-b0f4-48cd-ae8e-3e5b168ecd92)
- updateMetrics Function: updates the cache size metrics for pods, assumed pods, and nodes.
  ![image](https://github.com/user-attachments/assets/45031049-2184-41fc-aec4-164d923f6ba0)
