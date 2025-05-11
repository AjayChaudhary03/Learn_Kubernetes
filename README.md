# Learn_Kubernetes
My Kubernetes learning path

youtube video link : https://www.youtube.com/watch?v=X48VuDVv0do&t=3365s

Topics covered:
==============


|             Introduction                      |                   Advanced Topics                     |
|:----------------------------------------------|:------------------------------------------------------|
|    i.  What is Kubernetes                     |       i. K8s Namespaces - Organize your components    |
|    ii. Main K8s Components                    |       ii. K8s Ingress                                 |
|    iii.K8s Architecture                       |       iii.Helm - Package Manager                      |
|    iv. Minikube and Kubectl - Local Setup     |       iv. Volumes - Persisting Data in K8s            |
|    v.  Main Kubectl commands - K8s CLI        |       v.  K8s StatefulSet - Deploying Stateful Apps   |
|    vi. K8s YAML Configuration File            |       vi. K8s Services                                |


_________________________________________________________________________________________________________

# 1. What is Kubernetes
    Open source Container Orchestration tool
    i.e. Help in managing containerized applications in different deployment enviornments

    Why needed - Trend from Monolith to microservices... So there came a need where we can manage these microservces in better name than manual script runs.
    Features
        -  High availability or no downtime
        -  Scalability or high performace
        -  Disaster Recovery - Backup and restore

_________________________________________________________________________________________________________

# 2. Main K8s Components

##  POD
        - Smallest unit of K9s
        - Abstraction over container
        - Usually 1 application per pod
        - Each pod gets its own IP address - internal IP address
        - New IP address is assigned anytime pod is re-created. 
          - So, we can't rely on IPs alone to allow Pod communication with a node

##  SERVICE & INGRESS
* SERVICE
  - Permanent or static IP address attached to a pod
  - Lifecycle of SERVICE is not connected with POD i.e. if a POD goes down, the SERVICE (or static IP address still remains valid)
  - So, if pod is recreated,the preexisting SERVICE can be utlized to access the newly created POD is same way as before.
  - Types
    - EXTERNAL : When we want application to be accessible from browser i.e. from internet (outside of this K8s architecure)
    - INTERNAL : When we want application or resources like DB to be only allowed to access from internal K8s architecture.
  - Also, acts as Load Balancer to route request among available replicasets of the pod.

* INGRESS
  - Provides a user friendly dns or address for use with EXTERNAL SERVICE.
  - External world ==> Ingress ==> routes or forwards it to ==> External Service ==> your Application running in pod

![High level overview](./K8s%20Components_1.jpg)

* ConfigMap and Secret
  - DB end point : mondo-db-service
  - DB url usually lies in built application
  - if changes
- Secret
  - base64 encoded
  - passwords and certificates
- Use it as env variable or properties file

![High level overview](./K8s%20Components_2.jpg)

* Volumes - attaches a physical storage to your pod
  - **K8s doesn't manage data persistance. User or administator of cluster are responsible for data storage.**
  - Local i.e. stored locally on node within K8s 
  - Remote  - i.e. outside of K8s cluster e.g. on-premise

* Deployment
  - *Blueprint* for the application pods (**NOTE** : I didn't say database pods.)
    - i.e. Abstraction of Pods
  - In real world scenario, we create deployments rather than creating pods directly.
  - Why Databases can't be replicated through *Deployment*
    - Databases are Stateful applications i.e. they have a state (data)
    - So, there needs to be a some kind of mechanism where each node can access a common storage which is kept upto date for IO operations happening in DB inside nodes.

* StatefulSet 
  - *Blueprint* for the database pods
  - Ensures to keep track which pod is writing or reading data from the database. Thus eliminates data inconsistencies
  - not easy task 
    - DBs are often hosted outside of K8s cluster
 
![High level overview](./K8s%20Components_3.jpg)

_________________________________________________________________________________________________________

# 3. K8s Architecture

## Node Processes

3 Processess must be installed on every Node (worker node)

Container runtime (e.g. Docker)
Kubelet - Process that schedeudles those pods or containers underneath
  interacts with both the container as well the node.
  responsible for tking the configuraton and starting the pod or basically starting the container inside
  assigning resources like CPU or memory for running 

Kubeproxy 
  intelligent forwarding logic
  communication works in a perfomant way with  low overhead

![K8s Worker machine](./K8s%20Architecture_1.jpg)