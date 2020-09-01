- Monitor Cluster Components
    - Node level metrics
        - number of nodes
        - how many of them are healthy as well as performance metrics, CPU, Memory, network, disk utilization
    - POD level metrics
        - number of pods
        - CPU, memory
    - opensource
        - metrics server
            - have one metrics server per kubernetes cluster, retrieves metrics from each of kubernetes nodes and pods, aggregates them and store them in memory,
            - metrics server is only an in memory monitoring solution and does not store the metrics, 
            so you can not see historical performance data
        - prometheus
        - elastic stack 
        - data dog
    - kubelet containes subcomponent known as cAdvisor or Container advisor, responsible for retrieving performance metrics from pods, 
    and exposing them through the kubelet api
    
- Logs kubernetes
    - kubectl logs -f xxx-pod
    - if there are multiple containers within a pod, you must specify the name of container explicitly in the command   
        - kubectl logs -f xxx-pod xxx-container-name