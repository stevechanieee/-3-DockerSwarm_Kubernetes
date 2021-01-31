


Utilizing Two Orchestrators: Docker Swarm &amp; Kubernetes (TO_DSK)

Docker Swarm, by default, prioritizes isolation between containers. This is construed by some to represent higher security.

Kubernetes prioritizes communication between multiple containers in the same pod. This is construed by some to represent lower security.

Depending upon the preference, Kubernetes apps can be migrated to Docker Swarm, and vice versa.

Depending upon the requirement, the choice of orchestrator (i.e., Docker Swarm or Kubernetes) can be made.


For Kubernetes v1.20 and higher, Docker will be deprecated.



"OpenShift" typically refers to OpenShift Origin (a.k.a. OKD), which is an open source container application platform (developed by Red Hat) that is based upon Kubernetes (developed by Google) and Docker. "Red Hat OpenShift" refers to the repertoire of container orchestration developed by IBM Red Hat.

OpenShift is a polyglot platform that supports numerous languages.

Source: https://www.zdnet.com/article/red-hat-opens-new-openshift-platform-as-a-service-public-cloud/

Kubernetes is an open source container orchestration project. 

The Cloud Native Computing Foundation (CNCF) maintains the Kubernetes community, and volunteer administrators and volunteers engage in the maintenance, development, and new releases of Kubernetes


As the developer of Kubernetes, Google is consiered the first leading contributor to the Kubernetes project. Red Hat (which had worked with Google on Kubernetes prior to launch) is considered to be the second leading contributor to the Kubernetes project.


Kubernetes manages clusters (i.e., groups of containers). Each cluster has two constituent components: (1) control plane, and (2) worker nodes. Containers reside within the various worker nodes (each with its own Linux operating system). The control plane maintains the cluster’s state (e.g., which apps are running), whereas worker nodes handle the actual computational workload.


The attention surrounding container orchestration has shifted from Docker to Kubernetes. In fact, Docker itself adopted Kubernetes and announced native support for Kubernetes at DockerCon Europe in Copenhagen on 17 October 2017. However, Docker's architecture enables users to select the desired orchestration engine (Docker Swarm, Kubernetes) at run time.


