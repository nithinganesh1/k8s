
# Kubernetes

## Basics
k8s is a most popular container orchestration tool. 

Kubernetes is a tool that helps us to run and manage application in conainers. 

Developed by Google Lab in 2014 also know as k8s.

it is an open-source container orchestraction platform that automates the deployment, management, and scaling of container-based applications in diffrent kinds of environmnets like physical virtual and cloud-native computing fundations

containers are isolated from each other so that multiple containers can run on the same machine without interruting anyone else.

How to manage containers effectively
eg. a sheep captain for these containers

## history
created by google BORG to manage their linux containers, in mid-2014, kubernets realsed as an open source version of borg

Now managed by CNCF(Cloud Native Computing Foundation)

## Benefits
1. Automated deployment and management
2. Scalability
3. High availablity
    * High availablity for our application
    * reduce the latency isssues for the end users
4. Cost-effectiveness
    * reduce unnecessary use of infra 
5. Improved developers productivity

## Ohter Container Orchestration platform
1. Docker Swarm
2. OpenShift
3. Nomad

## Features of Kubernetes
1. Automated Scheduling / service discovery and load balancing
2. Self-Healing Capabilities
    * rescheduling, replacing and restarting the containers that are dead
3. Automated Rollouts and Rollbacks
4. Horizontal Scaling and Load Balancing
    * scale up and down the application as per the requirements
5. Best Resource Utilization
6. Seacreat and configuration management
7. Community Support
__________________________________
## Master node (control plane), Worker nodes

1. Master node 4 primery service in master node
   * Api Server
   * Scheduler
   * Controller manager
   * etcd
2. Worker node
   * kubelet
   * proxy
   * docker engine
## KUBE API SERVER

* enable communication across services
* exposes k8s API
* front end of the control plane
* kubectl cli commands is usesd to connect to kube api
* kubectli needed to be installed

## ETCD 
* key value store
* store the info about the k8s cluster
* Kube api stores and retrive data from the etcd Server
* store all runtime info and should be backed up regularly

## Schedule conatiner in the right node
watch for the request, scheduler will pick up the right node and send message "heii, you conainer"
factors to choose the right container

    1. Resource requirement
    2. hardware/software/policy constraints
    3. affinity and anti-affinity specifications(i need to run on a specific node or vise versa) ie, i want run this container or i don't want run this container run remening all.

## Controller manager
logically each controller is a seperate process to reducfe complexity, they are all compiled into a single binary and run in a single process it includes 
* node controller
* replication controller
* end point controller
* service account and token controller
* work node components

## Kubelet (agent)
listen to master requests or commands

runs in every nodes of a cluster, make sure that containers are running in a pod

when sheculer assigns a node, it assign kubelet to run it 

it pull the image and run the container 

## Kube proxy
network proxy that runs in every node in the cluster

can set network rules

## Container runtime environmnet

docker, rocket, containerD, kubernetes CRI(conainer Runtime interface)


# Pods

## pods an container relation 
* A VM is analogous to a pod, providing resources for processes to run.
* A VM offers all necessary resources (CPU, RAM, networking) for its services, while the processes utilize them.
* Similarly, pods supply all resources for containers to operate.Containers run within pods.
* In this analogy, the container represents the process, and the pod functions like a VM.
* There’s no traditional virtualization, but pods offer a level of isolation.

## why use pods insted of running containers directly
* Kubernetes can utilize different container runtime environments, providing flexibility in how containers are managed.

* Pods provide an abstraction layer, allowing for a standardized set of commands and configurations, making deployment easier and more consistent.

* You can access containers via podIP:port, simplifying network configurations and communication.

* A pod can host one or more containers, allowing for closely related processes to share resources and network space.

## should we run multiple containers in a pod

* depends
* idioly, there will be one container inside a pod, ohter container are hellper container
* pod will be distributed along multiple worker nodes
