# DSK #

The experimentation architecture utilizes two orchestrators: Docker Swarm and Kubernetes (DSK)

Docker Swarm, by default, prioritizes isolation between containers. This is construed by some to represent higher security.

Kubernetes prioritizes communication between multiple containers within the same pod. This is construed by some to represent higher efficacy, but lower security.

*Source: https://medium.com/opstalk/top-considerations-for-docker-ce-vs-ee-and-kubernetes-vs-swarm-9563a9c623ff*

Depending upon the preference, Kubernetes apps can be migrated to Docker Swarm, and vice versa.

Depending upon the requirement, the choice of orchestrator (i.e., Docker Swarm or Kubernetes) can be made explicitly. Alternatively, an Artificial Intelligence (AI) engine can be utilized to make the decision depending upon the need.

For Kubernetes v1.20 and higher, Docker will be deprecated.

For convenience, the more recent Kubernetes release version documentation maintenance status is provided below in Table 1:

### Table 1: Kubernetes Release Version Documentation Maintenance Status ###

|Kubernetes Release Version|Version Documentation Maintenance Status                     |
|--------------------------|-------------------------------------------------|
|Kubernetes v1.20          | documentation is maintained.                    |
|Kubernetes v1.19          | documentation is no longer actively maintained. |
|Kubernetes v1.18          | documentation is no longer actively maintained. |
|Kubernetes v1.17          | documentation is no longer actively maintained  |
|Kubernetes v1.16          | documentation is no longer actively maintained. |

*Source: https://kubernetes.io/docs/home/supported-doc-versions/*<br/>
*Source: https://v1-19.docs.kubernetes.io/docs/home/supported-doc-versions/*<br/>
*Source: https://v1-18.docs.kubernetes.io/docs/home/supported-doc-versions/*<br/>
*Source: https://v1-17.docs.kubernetes.io/docs/home/supported-doc-versions/*<br/>
*Source: https://v1-16.docs.kubernetes.io/docs/home/supported-doc-versions/*<br/>

Red Hat OpenShift Container Platform (RHBA-2020:4196) release version uses Kubernetes v1.19 (https://v1-19.docs.kubernetes.io/docs/setup/release/notes/) with Container Runtime Interface (CRI) plus Open Container Initiative (OCI) (a.k.a. CRI-O) container runtime (Docker is deprecated).

By way of background information, CRI-O is an implementation of the Kubernetes Container Runtime Interface, which enables the utilization of the OCI compatible runtimes. CRI-O can pull from any container registry (a repository of Docker and OCI images) and supports OCI container images. 

*Source: https://www.redhat.com/en/topics/cloud-native-apps/what-is-a-container-registry*

A Docker container image is a lightweight (the container shares the machine's Operating System or OS system kernel; hence, it does not require an OS per application, and thereby segues to higher server efficiencies), standalone, executable package of software that includes all the dependencies needed to run an application in the chosen computing environment: code, runtime, system tools, system libraries, and settings. Container images become containers at runtime (e.g., a Docker image can run on any OCI-compliant container runtin, such as CRI-O.

*Source: https://www.docker.com/resources/what-container*

Given that Docker is deprecated as a container runtime after v1.20, a replacement supported container runtime is needed (e.g., containerd or CRI-O).

*Source: https://kubernetes.io/blog/2020/12/02/dont-panic-kubernetes-and-docker/*

Despite its deprecation, it can still be utilized for building container images, such as within the involved Continuous Integration and Continuous Delivery/Deployment (CI/CD or CICD) pipeline. By way of background information, in software engineering, CI/CD or CICD generally refers to the combined practices of continuous integration and either continuous delivery or continuous deployment. "CI/CD bridges the gaps between development and operational activities and teams by enforcing automation in building, testing, and deployment of applications."

*Source: https://www.splunk.com/en_us/blog/devops/observability-with-ci-cd-in-a-developer-world.html*

CD Is The Practice That Focuses On Producing Release-Ready Software w/ Every Code Change.

Continuous integration (CI) is a software engineering practice where members of a team integrate their work with increasing frequency. ... Continuous delivery (CD) is to packaging and deployment what CI is to build and test.

CI and CD are two acronyms frequently used in modern development practices and DevOps. CI stands for continuous integration, a fundamental DevOps best








The Kubelet is the primary "node agent" that runs on each node. The Kubelet describes a pod, as does a PodSpec (a YAML or JSON object that describes a pod). The Kubelet is responsible for maintaining a set of pods, which are composed of one or more containers, on a local system. 


JavaScript Object Notation (JSON) is an open standard file format for storing and exchanging data.

YAML Ain't Markup Language (YAML) is a strict superset of JSON and is a file format for storing and exchanging data.


Kubernetes does not interact directly with Docker. Rather, Kubelet interacts with a layer entitled, "Dockershim."


Kubelet -> Dockershim -> Docker -> Containerd -> Containers


Kubelet -> CRI-Containered -> Containerd  (Containered 1.0)

Kubelet -> Containerd (with CRI plugin)   (Containered 1.1)

Source: https://kubernetes.io/blog/2018/05/24/kubernetes-containerd-integration-goes-ga/

"OpenShift" typically refers to OpenShift Origin (a.k.a. OKD), which is an open source container application platform (developed by Red Hat) that is based upon Kubernetes (developed by Google) and Docker. "Red Hat OpenShift" refers to the repertoire of container orchestration developed by IBM Red Hat.

OpenShift is a polyglot platform that supports numerous languages.

Source: https://www.zdnet.com/article/red-hat-opens-new-openshift-platform-as-a-service-public-cloud/

Kubernetes is an open source container orchestration project. 

The Cloud Native Computing Foundation (CNCF) maintains the Kubernetes community, and volunteer administrators and volunteers engage in the maintenance, development, and new releases of Kubernetes


As the developer of Kubernetes, Google is consiered the first leading contributor to the Kubernetes project. Red Hat (which had worked with Google on Kubernetes prior to launch) is considered to be the second leading contributor to the Kubernetes project.


Kubernetes manages clusters (i.e., groups of containers). Each cluster has two constituent components: (1) control plane, and (2) worker nodes. Containers reside within the various worker nodes (each with its own Linux operating system). The control plane maintains the cluster’s state (e.g., which apps are running), whereas worker nodes handle the actual computational workload.


The attention surrounding container orchestration has shifted from Docker to Kubernetes. In fact, Docker itself adopted Kubernetes and announced native support for Kubernetes at DockerCon Europe in Copenhagen on 17 October 2017. However, Docker's architecture enables users to select the desired orchestration engine (Docker Swarm, Kubernetes) at run time.


