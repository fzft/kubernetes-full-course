- OS Upgrade
    - if the node was down for more than 5 mins, then the pods are terminated from that that node, 
    kubernetes considers them as dead, if the PODs where part of a relicaset, then they are recreated on other nodes 
    - the time it waits for a pod to come back online is known as the pod eviction timeout and is set as the controller manager
    with default value 5mins
    - when the nodes come back, without any pods scheduled
    - if you have maintenance tasks to be performed on a node , make a quick upgrade and reboot
    - drain the node of all the workloads to other nodes
    - the node is also cordoned or marked as unschedulable until remove the restriction
    - when reboot, need to uncordon it 
- Backup and restore
    - github
    - Velero
    - ETCD
        - master node