# Learn_Kubernetes
My Kubernetes learning path

youtube video link : https://www.youtube.com/watch?v=X48VuDVv0do&t=3365s

Topics covered:
==============
A. Introduction
    i.  What is Kubernetes
    ii. K8s Architecture
    iii.Main K8s Components
    iv. Minikube and Kubectl - Local Setup
    v.  Main Kubectl commands - K8s CLI
    vi. K8s YAML Configuration File
B . Advanced Topics
    1. K8s Namespaces - Organize your components
    2. K8s Ingress
    3. Helm - Package Manager
    4. Volumes - Persisting Data in K8s
    5. K8s StatefulSet - Deploying Stateful Apps
    6. K8s Services
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