# DSK #

The experimentation architecture utilizes two container orchestration platforms: Docker Swarm (a.k.a. Swarm) and Kubernetes (collectively, SK).

Docker Swarm, by default, prioritizes isolation between containers. This is construed by some to represent higher security.

Kubernetes prioritizes communication between multiple containers within the same pod. This is construed by some to represent higher efficacy, but lower security.

*Source: https://medium.com/opstalk/top-considerations-for-docker-ce-vs-ee-and-kubernetes-vs-swarm-9563a9c623ff*

Depending upon the preference, Kubernetes apps can be migrated to Docker Swarm, and vice versa.

Depending upon the requirement, the choice of orchestrator (i.e., Docker Swarm or Kubernetes) can be made explicitly. Alternatively, an Artificial Intelligence (AI) engine can be utilized to make the decision depending upon the need.

Over the past several years, the leadership for container orchestration, potentially, has shifted from Docker to Kubernetes. In fact, Docker itself adopted Kubernetes and announced native support for Kubernetes at DockerCon Europe in Copenhagen on 17 October 2017. However, Docker's architecture enables users to select the desired orchestration engine (Docker Swarm, Kubernetes) at runtime.

Kubernetes is an open source container orchestration project; moreover, Kubernetes manages clusters (i.e., groups of containers). Each cluster has two constituent components: (1) control plane, and (2) worker nodes. Containers reside within the various worker nodes (each with its own Linux operating system). The control plane maintains the cluster’s state (e.g., which apps are running), whereas worker nodes handle the actual computational workload. The Cloud Native Computing Foundation (CNCF) maintains the Kubernetes community, and volunteer administrators and volunteers engage in the maintenance, development, and new releases of Kubernetes. As the original developer of Kubernetes, Google is considered the first leading contributor to the Kubernetes project. Red Hat (which had worked with Google on Kubernetes prior to launch) is considered to be the second leading contributor to the Kubernetes project.

For Kubernetes v1.20 and higher, Docker will be deprecated.

*Source: https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG/CHANGELOG-1.20.md#deprecation*

For convenience, the more recent Kubernetes release version documentation maintenance status is provided below in Table 1:

### Table 1: Kubernetes Release Version Documentation Maintenance Status ###

|Kubernetes Release Version|Version Documentation Maintenance Status                     |
|--------------------------|-------------------------------------------------|
|**Kubernetes v1.20**          | documentation is maintained.                    |
|Kubernetes v1.19          | documentation is no longer actively maintained. |
|Kubernetes v1.18          | documentation is no longer actively maintained. |
|Kubernetes v1.17          | documentation is no longer actively maintained  |
|Kubernetes v1.16          | documentation is no longer actively maintained. |

*Source: https://kubernetes.io/docs/home/supported-doc-versions/*<br/>
*Source: https://v1-19.docs.kubernetes.io/docs/home/supported-doc-versions/*<br/>
*Source: https://v1-18.docs.kubernetes.io/docs/home/supported-doc-versions/*<br/>
*Source: https://v1-17.docs.kubernetes.io/docs/home/supported-doc-versions/*<br/>
*Source: https://v1-16.docs.kubernetes.io/docs/home/supported-doc-versions/*<br/>

"OpenShift" typically refers to OpenShift Origin (a.k.a. OKD), which is an open source container application platform (developed by Red Hat) that is based upon Kubernetes (developed by Google) and Docker. "Red Hat OpenShift" refers to the repertoire of container orchestration tools developed by IBM Red Hat.

Source: https://www.zdnet.com/article/red-hat-opens-new-openshift-platform-as-a-service-public-cloud/

The IBM Red Hat OpenShift Container Platform (RHBA-2020:4196) release version uses Kubernetes v1.19 (https://v1-19.docs.kubernetes.io/docs/setup/release/notes/) with Container Runtime Interface (CRI) plus Open Container Initiative (OCI) (a.k.a. CRI-O) container runtime. By way of background information, CRI-O is an implementation of the Kubernetes Container Runtime Interface, which enables the utilization of the OCI compatible runtimes. CRI-O can pull from any container registry (a repository of Docker and OCI images) and supports OCI container images. 

*Source: https://www.redhat.com/en/topics/cloud-native-apps/what-is-a-container-registry*

A Docker container image is a lightweight (the container shares the machine's Operating System or OS system kernel; hence, it does not require an OS per application, and thereby segues to higher server efficiencies), standalone, executable package of software that includes all the dependencies needed to run an application in the chosen computing environment: code, runtime, system tools, system libraries, and settings. Container images become containers at runtime (e.g., a Docker image can run on any OCI-compliant container runtime, such as CRI-O).

*Source: https://www.docker.com/resources/what-container*

Given that Docker is deprecated as a container runtime from Kubernetes v1.20 and higher, a replacement supported container runtime is needed (e.g., containerd or CRI-O).

*Source: https://kubernetes.io/blog/2020/12/02/dont-panic-kubernetes-and-docker/*

To clarify the relationship between containerd, Docker, and Kubernetes, please note that Kubernetes does not interact directly with Docker. Rather, Kubernetes (via Kubelet) interacts with a layer entitled "Dockershim" as shown in Figure 1 below, and a lexicon primer is provided in Figure 2 below. In addition, please note that the Kubelet is the lowest level component in Kubernetes; it can be compared to a process watcher, but focused on running containers. A pod is a collection of containers, and the pod is the unit of execution for Kubernetes.

### Figure 1: Kubernetes (via Kubelet) interaction with Docker (via Dockershim) and interaction with Containers (via Containerd) ###

Kubelet -> Dockershim -> Docker -> Containerd -> Containers

### Figure 2: Lexicon Primer ###

* The Kubelet is the primary "node agent" that runs on each node. The Kubelet describes a pod, as does a PodSpec (a YAML or JSON object that describes a pod). The Kubelet is responsible for maintaining a set of pods, which are composed of one or more containers, on a local system. 

* JavaScript Object Notation (JSON) is an open standard file format for storing and exchanging data.

* YAML Ain't Markup Language (YAML) is a strict superset of JSON and is a file format for storing and exchanging data.

However, Containered (v1.0) was end-of-lifed, and in Containered (v1.1), the CRI-Containerd daemon was refactored (i.e., restructuring the internal structure of an existing body of code without altering the external behavior) to be a CRI plugin, as shown in Figure 3 below.

### Figure 3: CRI-Containerd Refactored
Original: Kubelet -> CRI-Containerd -> Containerd -> Containers  (Containerd 1.0)

Refactored: Kubelet -> Containerd (with CRI plugin) -> Containers  (Containerd 1.1)

*Source: https://kubernetes.io/blog/2018/05/24/kubernetes-containerd-integration-goes-ga/*

Docker Engine (described by Docker as "the underlying tooling/client that enables users to easily build, manage, share and run their container objects on Linux") is built on top of containerd. Docker CE (Community Edition) is the classical open source Docker Engine. The next release of Docker Community Edition (Docker CE) will use containerd version 1.1. 

*Source: https://www.docker.com/blog/introducing-docker-engine-20-10/*
*Source: https://kubernetes.io/blog/2018/05/24/kubernetes-containerd-integration-goes-ga/*

Despite its deprecation, it can still be utilized for building container images, such as within the involved Continuous Integration and Continuous Delivery/Deployment (CI/CD or CICD) pipeline. By way of background information, in software engineering, CI/CD or CICD generally refers to the combined practices of Continuous Integration (CI) and either Continuous Delivery (CD) or Continuous Deployment (CD). Taken individually, CI is a software engineering practice whereby members of a team integrate their work with increasing frequency, and CD is a software engineering practice whereby members of a team focus on packaging and deploying what CI has built and tested. As a Splunk blog article re-cites from Wiki, "CI/CD bridges the gaps between development and operational activities and teams by enforcing automation in building, testing, and deployment of applications." In fact, CI/CD has become a Software Development (Dev) and Information Technology (IT) Operations (Ops) (collectively, DevOps) best practice.

*Source: https://www.splunk.com/en_us/blog/devops/observability-with-ci-cd-in-a-developer-world.html*

In summary, CI/CD is a practice of producing release-ready software with every code change.

*Source: https://stackify.com/continuous-delivery-vs-continuous-deployment-vs-continuous-integration/*

Given the continued benefit of Docker for CI/CD and the fact that both Docker and CRI-O are underpinned by containered, it seems that both have a value-added proposition. Moreover, Docker, CRI-O, and containerd all depend on **runC** at the lowest level to effectuate the running of containers.

*Source: https://computingforgeeks.com/docker-vs-cri-o-vs-containerd/*

### Interim Finding ###

* A multi-faceted approach involving both Docker and CRI-O seems prudent, particularly given their mutual **runC** dependency, and the fact that Docker images are more prevalent for certain facets of the architectural stack.





