


Utilizing Two Orchestrators: Docker Swarm &amp; Kubernetes (TO_DSK)

Docker Swarm, by default, prioritizes isolation between containers. This is construed by some to represent higher security.

Kubernetes prioritizes communication between multiple containers in the same pod. This is construed by some to represent lower security.

Depending upon the preference, Kubernetes apps can be migrated to Docker Swarm, and vice versa.

Depending upon the requirement, the choice of orchestrator (i.e., Docker Swarm or Kubernetes) can be made.


For Kubernetes v1.20 and higher, Docker will be deprecated.



"OpenShift" typically refers to OpenShift Origin (a.k.a. OKD), which is an open source container application platform (developed by Red Hat) that is based upon Kubernetes (developed by Google) and Docker. the downstream container orchestration technology derived from the OKD open source project (previously known as OpenShift Origin). "Red Hat OpenShift" refers to the suite of container orchestration products by Red Hat.



Kubernetes is an open source container orchestration project. It helps users manage clustered groups of hosts running Linux containers, which are sets of processes that contain everything needed to run in isolation.

Kubernetes was originally developed and designed by engineers at Google—one of the early contributors to Linux container technology—before it was donated to the Cloud Native Computing Foundation (CNCF) in 2015. That means that the CNCF is the entity responsible for maintaining the Kubernetes community, while volunteer contributors and administrators are responsible for Kubernetes development, maintenance, and releases.

Red Hat was one of the first companies to work with Google on Kubernetes—even prior to launch—and has since become the second leading contributor to the Kubernetes project.


Kubernetes both manage groups of containers called clusters. Each cluster has 2 parts: a control plane and worker nodes. Containers run in the worker nodes, each of which has its own Linux operating system. The control plane maintains the cluster’s overall state (like what apps are running and which container images are used), while worker nodes do the actual computing work.



Kubernetes can do, users still need to integrate other components like networking, ingress and load balancing, storage, monitoring, logging, and more. Red Hat OpenShift offers these components with Kubernetes at their core because—by itself— Kubernetes is not enough.




The Community Distribution of Kubernetes that powers Red Hat OpenShift



