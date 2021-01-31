


Utilizing Two Orchestrators: Docker Swarm &amp; Kubernetes (TO_DSK)

Docker Swarm, by default, prioritizes isolation between containers. This is construed by some to represent higher security.

Kubernetes prioritizes communication between multiple containers in the same pod. This is construed by some to represent lower security.

Depending upon the preference, Kubernetes apps can be migrated to Docker Swarm, and vice versa.

Depending upon the requirement, the choice of orchestrator (i.e., Docker Swarm or Kubernetes) can be made.


For Kubernetes v1.20 and higher, Docker will be deprecated.


Red Hat OpenShift Container Platform (RHBA-2020:4196) release uses Kubernetes 1.19 (https://v1-19.docs.kubernetes.io/docs/setup/release/notes/) with CRI-O runtime (Docker is deprecated).


CRI-O is an implementation of The Kubernetes Container Runtime Interface, which enables the utilization of the Open Container Initiative (OCI) compatible runtimes is referred to as CRI-O. CRI-O can pull from any container registry and supports OCI container images. 

A Docker container image is a lightweight (the container shares the machine's OS system kernel; hence, it does not require as OS per application, and thereby segues to higher server efficiencies), standalone, executable package of software that includes all the dependencies needed to run an application in the chosen computing environment: code, runtime, system tools, system libraries and settings. Container images become containers at runtime.


Docker builds an OCI-standard container image. That means a Docker image can run fine on any OCI-compliant container runtime — that includes both containerd and CRI-O.

If you’re using Docker as a container runtime within your Kubernetes cluster, you’re impacted. You’ll have to replace it with a supported container runtime — containerd or CRI-O. Docker containers run perfectly fine on both.

Apart from being a container runtime, it’s also a developer-friendly container engine. So if you’re using Docker for building container images and within your CI/CD pipeline, you can continue to use it.

n software engineering, CI/CD or CICD generally refers to the combined practices of continuous integration and either continuous delivery or continuous deployment. CI/CD bridges the gaps between development and operation activities and teams by enforcing automation in building, testing and deployment of applications.

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


