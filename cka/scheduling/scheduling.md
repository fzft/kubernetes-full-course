- Scheduling
    - yaml property set: nodeName
        - the scheduler goes through all the pods and looks for those that do not have this property set
        those are the candidates for the scheduling, then it identified the right node of the POD by some algorithm, 
        once identified it schedules the POD on the node by setting the node Name property 
    - no scheduler 
        - pod status: pending
        - you can manually assign pods to node yourself
            - set the nodeName field to the name of the node (in creation time)
            - create a binding object and send a post request to the pod binding API (exist pod)
            ![image info](binding-yaml.jpg)
            
- Labels and Selectors
    - group and select objects use labels and selectors
    
- Taints And tolerations
    - set restriction on what pods can be scheduled on a node
    - taints are set on nodes and tolerations are set on pods
    - Tains-Node
        - kubectl taint nodes node-name key=value:taint-effect
        - taint-effect
            - NoSchedule
            - PreferNoSchedule
                - system will try to avoid placing a pod on the node, but that is not guaranteed
            - NoExecute
                - new pods will not be scheduled on the node
                - the existing pods on the node if any
                will be evicted if they do not tolerate the taint
    - Tolerations-PODs
        ![image info](tolerations-pod.jpg)
    - the scheduler does not schedule any pods on the master node, when the kubernetes cluster is first set up,
    a taint is set on the master node automatically, that prevents any pods from being scheduled on this node
- Node selector