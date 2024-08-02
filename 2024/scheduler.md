**Metric Recorder:**
- Struct 
![image](https://github.com/user-attachments/assets/d19e021d-fc81-44c0-8409-39b28b6e46c5)
- Constructor: NewMetricsAsyncRecorder instantiates and returns a new MetricAsyncRecorder object, and starts a goroutine to record the metrics.
![image](https://github.com/user-attachments/assets/7e2c579b-0c1d-4900-a68e-fb5c4a86475f)
- Method:
![image](https://github.com/user-attachments/assets/e6b5fefa-9ea3-45c1-8c8d-94eb48dd4c33)
Metric is recorded asynchronously
![image](https://github.com/user-attachments/assets/c384d5e4-f2e3-428b-ad17-9312ed1b3c44)

**Cache**
- State Machine of a pod's events in scheduler's cache:
![image](https://github.com/user-attachments/assets/7b97508d-9f94-4d5c-b0ae-59e9eeb032a5)
- Cache Interface: Cache provides various methods to manipulate pods and nodes within the cache:
  NodeCount: Returns the number of nodes in the cache.
  PodCount: Returns the number of pods in the cache.
  AssumePod: Assumes that a pod has been scheduled and aggregates the pod's information into the corresponding node.
  FinishBinding: Signals that the cache for the assumed pod can be expired.
  ForgetPod: Removes an assumed pod from the cache.
  AddPod: Confirms or adds back a pod if it has expired.
  UpdatePod: Removes the old pod's information and adds the new pod's information.
  RemovePod: Removes a pod and subtracts the pod's information from the assigned node.
  GetPod: Returns the pod from the cache with the same namespace and name.
  IsAssumedPod: Checks if the pod is assumed and not expired.
  AddNode: Adds overall information about the node.
  UpdateNode: Updates overall information about the node.
  RemoveNode: Removes overall information about the node.
  UpdateSnapshot: Updates the snapshot of the current node information in the cache.
  Dump: Produces a dump of the current cache state.
