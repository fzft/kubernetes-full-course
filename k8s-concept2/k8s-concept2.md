- POD with Yaml
    - yaml file definition file contains 4 top level field (required field)
        - apiVersion
            - version of the kubernetes API you're using to create the objects,
            depending on what we are trying to create we must use the right API version
            -
            |  Kind   | Versuib  |
            |  ----  | ----  |
            | POD | v1 |
            | Service | v1 |
            | ReplicaSet  | app/v1 |
            | Deployment | app/v1|
            - type: string
        - kind
            - refers to the type of object we are trying to create
            - replicaSet, deployment, service
            - type: string
        - metadata
            - metadata is data about the object like its name, labels, etc
            - you can only specify name or labels or anything else that kubernetes expects to be under metadata,
            you can not add any other property as you wish under this
            - type: Dictionary
            - structure
                - name
                    - type: string
                - lables
                    - under lables you can have any kind of key or value pairs as you see fit
                    - type Dictionary
            - relationship
                - name and labels are sibling
        - spec
            - specification section 
            - providing additional information to kubernetes pertaining to that obejct
            - type: Dictionary
            - structure
                - containers
                    - type: list (the parts can have multiple containers within it)
    - create
        - kubectl create -f pod-definition.yml

- Controller
    - brain behind kubernetes, they are the processes that monitor kubernetes objects and respond accordingly
    - Replication Controller
        - usage
            - HA
                - run multiple instance of a single pod in the kubernetes cluster, providing HA
                - even if you have single pod, the replication controller can help by automatically bring up a new pod when the existing one fails,
                thus the replication controller ensures that specified number of pods are running at all times
            - Load Balancing & Scaling
                - the replication controller spans across multiple nodes in the cluster
        - configuration
            - spec 
                - template
                    - create a template section under spec to provide a pod template to be use
                - replicas
                    - type: int
- ReplicaSet
    - apiVersion
        - apps/v1
    -spec
        - selector
            - helps the replica set identify what pods fall under it, replica set can also manage pods that
            were not created as part of the replica set creation
            - eg: there were pods created before the creation of the replica set that match labels specified in the selector,
            the replica set will also take those pods into consideration when creating the replicas
            - structure
                - matchLabels
                    - simply matches the labels specified under it to the labels on the pod
                    - as a filter for replica set, under the selector section , matchLabel filter and provide the same label used while creating the pods
                    
    - Scale
        - update the number of replicas in the definition file to six
            - kubectl replace -f xxx.yml
        - kubectl scale --replicas=6 -f xxx.yml
        
 - Deployment
    - first create a deployment it triggers a rollout, a new rollout creates a new deployment reversion, in the 
    future when the application is upgrade meaning when the container version is updated to a new one, a new rollout is triggered and a new deployment reversion is created,
    help us keep track of the changes made to our deployment and enables us to roll back a previous version of deployment
    - rollouts
    - versioning        
    - Rollout Command
        - kubectl rollout status deployment/myapp-deployment
        - kubectl rollout history deployment/myapp-deployment
            - show the reversions and history of our deployment
    - strategy
        - recreate strategy
            - first destroy and deploy new instances of new version 
            - disadvantage
                - during the period down and up, the application is down and inaccessible
        - rolling update (default deployment strategy)
            - take down the older version and bring up a newer version one by one 
            - advantage
                - the application never goes down and the upgrade is seamless
    - Command
        - kubectl apply 
    - rollback 
        - kubectl rollout undo deployment/myapp-deployment
        
            
         
