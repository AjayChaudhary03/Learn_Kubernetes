# Learn_Kubernetes
My Kubernetes learning path

youtube video link : https://www.youtube.com/watch?v=X48VuDVv0do&t=3365s

Topics covered:
==============

|               Introduction                    |                 Advanced Topics                       |
|--------------------------------------------- :|------------------------------------------------------:|
|                                               |                                                       |
|    i.  What is Kubernetes                     |       i. K8s Namespaces - Organize your components    |
|    ii. K8s Architecture                       |       ii. K8s Ingress                                 |
|    iii.Main K8s Components                    |       iii.Helm - Package Manager                      |
|    iv. Minikube and Kubectl - Local Setup     |       iv. Volumes - Persisting Data in K8s            |    
|    v.  Main Kubectl commands - K8s CLI        |       v.  K8s StatefulSet - Deploying Stateful Apps   |
|    vi. K8s YAML Configuration File            |       vi. K8s Services                                |


=======================================================

# 1. What is Kubernetes
    Open source Container Orchestration tool
    i.e. Help in managing containerized applications in different deployment enviornments

    Why needed - Trend from Monolith to microservices... So there came a need where we can manage these microservces in better name than manual script runs.
    Features
        -  High availability or no downtime
        -  Scalability or high performace
        -  Disaster Recovery - Backup and restore

# 2. K8s Architecture


    ## POD
        - Smallest unit of K9s
        - Abstraction over container
        - Usually 1 application per pod
        - Each pod gets its own IP address - internal IP address
        - New IP address is assigned anytime pod is re-created. 
          - So, we can't rely on IPs alone to allow Pod communication with a node

    ## SERVICE & INGRESS