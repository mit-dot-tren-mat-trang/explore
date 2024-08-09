# Scheduling Framework
![image](https://github.com/user-attachments/assets/157114e2-482d-464a-83e2-f97cb55d949d)
## Image locality
Favors nodes that already have the container images that the Pod runs. Extension points: score.
![image](https://github.com/user-attachments/assets/8d19d854-5a50-4f1a-87e2-1613672e61de)
![image](https://github.com/user-attachments/assets/79a05fc5-cd7a-49fc-8ff7-47b0fc5cbc12)
## Taint toleration
Implements taints and tolerations. Implements extension points: filter, preScore, score.
![image](https://github.com/user-attachments/assets/2e6aa965-8eea-40ad-911c-b763244d3642)
![image](https://github.com/user-attachments/assets/f5c91da1-a4f7-4d97-b89c-23b30b55a17e)
![image](https://github.com/user-attachments/assets/11797679-500c-4143-9938-ec615e7bb714)
![image](https://github.com/user-attachments/assets/7a1abd80-c317-4d54-9907-785958f18b25)
![image](https://github.com/user-attachments/assets/027a7b42-996f-4f4b-bac6-df130a9c4630)
![image](https://github.com/user-attachments/assets/3e0ca5c9-f17d-4339-9cb5-e19a3dca8477)
## Node name
Checks if a Pod spec node name matches the current node. Extension points: filter.
![image](https://github.com/user-attachments/assets/ea26ec26-5999-479f-87b4-f8c7c6b7efb9)
## Node ports
Checks if a node has free ports for the requested Pod ports. Extension points: preFilter, filter.
![image](https://github.com/user-attachments/assets/8d26f84c-0585-4e57-8350-64e967c17b34)
![image](https://github.com/user-attachments/assets/fdb9841f-135f-45a7-863e-d4429ceefc30)
## NodeAffinity 
Implements node selectors and node affinity. Extension points: filter, score.
![image](https://github.com/user-attachments/assets/b982d9df-edc4-4a38-9a3e-8abf759f4a78)
![image](https://github.com/user-attachments/assets/450d94f3-1d03-4174-9a8c-009ab6f4554d)
## PodTopologySpread 
Implements Pod topology spread. Extension points: preFilter, filter, preScore, score, normalizedScore.
![image](https://github.com/user-attachments/assets/b2fd1bef-815a-4ac5-b08b-43bd7adbecce)
![image](https://github.com/user-attachments/assets/c36f8fea-1d0d-4da5-90d3-d3f7a285d1dc)
![image](https://github.com/user-attachments/assets/8731e4cf-a4bb-4644-b8b9-b5bb8da70859)
![image](https://github.com/user-attachments/assets/08b3d257-a661-466b-9201-f5f84341adeb)
![image](https://github.com/user-attachments/assets/ab1e5c9a-ec52-4cc4-9f95-0dde3df92950)
![image](https://github.com/user-attachments/assets/6c55b505-66fb-4410-abcd-ad203cf4e899)
![image](https://github.com/user-attachments/assets/7beed242-ca7f-493c-9e7e-1a3127e5e242)
![image](https://github.com/user-attachments/assets/874bbe51-36cf-4b2e-bfb5-f292f429bb5a)
![image](https://github.com/user-attachments/assets/862b3a84-c581-404c-a97b-78b91cd86698)
![image](https://github.com/user-attachments/assets/37208d2e-afb4-45a4-8e56-409b378c1f69)
## NodeUnschedulable 
Filters out nodes that have .spec.unschedulable set to true. Extension points: filter.
![image](https://github.com/user-attachments/assets/e4d493ac-712a-4587-816e-a504173763cc)
## NodeResourcesFit 
Checks if the node has all the resources that the Pod is requesting. The score can use one of three strategies: LeastAllocated (default), MostAllocated and RequestedToCapacityRatio. Extension points: preFilter, filter, score.
- LeastAllocated
  ![image](https://github.com/user-attachments/assets/e268253b-fee2-4324-95ad-80271b8dde1a)
- MostAllocated
  ![image](https://github.com/user-attachments/assets/5dcadd6b-1a75-4a20-9810-842dffca4bb3)
- RequestedToCapacityRatio
  ![image](https://github.com/user-attachments/assets/6f7160ab-1b53-48f5-b604-986a6cd69ffb)
## NodeResourcesBalancedAllocation 
Favors nodes that would obtain a more balanced resource usage if the Pod is scheduled there. Extension points: score.
![image](https://github.com/user-attachments/assets/8204ebbe-0f66-4b2f-95ef-ea7aac5f72a6)
