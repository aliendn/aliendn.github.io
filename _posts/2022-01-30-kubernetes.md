---
title: kubernetes and how to create some service like this
tags: [cloud, internet, kubernetes, gcloud, docker]
style: fill
color: info
description: Kubernetes, or K8s for short, is an open-source container-orchestration tool designed by Google. It's used for bundling and managing clusters of containerized applications — a process known as 'orchestration' in the computing world. The name Kubernetes originates from Greek, meaning helmsman or pilot.
---

{% include elements/figure.html image="https://kubernetes.io/images/kubernetes-horizontal-color.png" %}


# What is Kubernetes?

With the widespread adoption of containers among organizations, Kubernetes, the container-centric management software, has become the de facto standard to deploy and operate containerized applications. Google Cloud is the birthplace of Kubernetes—originally developed at Google and released as open source in 2014. Kubernetes builds on 15 years of running Google's containerized workloads and the valuable contributions from the open source community. Inspired by Google’s internal cluster management system, Kubernetes makes everything associated with deploying and managing your application easier. Providing automated container orchestration, Kubernetes improves your reliability and reduces the time and resources attributed to daily operations.

[Learn more about GKE, Google Cloud’s managed Kubernetes.](https://cloud.google.com/kubernetes-engine)

# Large-scale cluster management at Google with Borg

Google's Borg system is a cluster manager that runs hundreds of thousands of jobs, from many thousands of different applications, across a number of clusters each with up to tens of thousands of machines.

It achieves high utilization by combining admission control, efficient task-packing, over-commitment, and machine sharing with process-level performance isolation. It supports high-availability applications with runtime features that minimize fault-recovery time, and scheduling policies that reduce the probability of correlated failures. Borg simplifies life for its users by offering a declarative job specification language, name service integration, real-time job monitoring, and tools to analyze and simulate system behavior.

# Kubernetes vs. Docker

Docker is a containerization platform and runtime and Kubernetes is a platform for running and managing containers from many container runtimes. Kubernetes supports numerous container runtimes, including Docker. 

{% include elements/figure.html image="https://wac-cdn.atlassian.com/dam/jcr:1612c84e-cf8e-4eab-9444-e94e01e84175/Kubernetes-vs-Docker_1@2x.jpg?cdnVersion=746
" %}

While Docker is a container runtime, Kubernetes is a platform for running and managing containers from many container runtimes. Kubernetes supports numerous container runtimes including Docker, containerd, CRI-O, and any implementation of the Kubernetes CRI (Container Runtime Interface). A good metaphor is Kubernetes as an “operating system” and Docker containers are “apps” that you install on the “operating system”. 

On its own, Docker is highly beneficial to modern application development. It solves the classic problem of “works on my machine” but then nowhere else. The container orchestration tool Docker Swarm is capable of handling a production container workload deployment of a few containers. When a system grows and needs to add many containers networked to each other, standalone Docker can face some growing pains that Kubernetes helps address.

When comparing the two, a better comparison is of Kubernetes with Docker Swarm. Docker Swarm, or Docker swarm mode, is a container orchestration tool like Kubernetes, meaning it allows the management of multiple containers deployed across multiple hosts running the Docker server. Swarm mode is disabled by default and is something that needs to be setup and configured by a DevOps team.

Kubernetes orchestrates clusters of machines to work together and schedules containers to run on those machines based on their available resources. Containers are grouped together, through declarative definition, into pods, which is the basic unit of Kubernetes. Kubernetes automatically manages things like service discovery, load balancing, resource allocation, isolation, and scaling your pods vertically or horizontally. It has been embraced by the open source community and is now part of the Cloud Native Computing Foundation. Amazon, Microsoft, and Google all offer managed Kubernetes services on their cloud computing platforms, which significantly reduces the operational burden of running and maintaining Kubernetes clusters and their containerized workloads.

# Docker or Kubernetes: Which one is right for you?

{% include elements/figure.html image="https://wac-cdn.atlassian.com/dam/jcr:8a8c5eff-cedd-4e46-a397-9d635a098afc/Kubernetes-vs-Docker-article_2@2x.jpg?cdnVersion=746" %}

So if both Docker Swarm and Kubernetes are container orchestration platforms, which do you choose?

Docker Swarm typically requires less setup and configuration than Kubernetes if you’re building and running your own infrastructure. It offers the same benefits as Kubernetes, like deploying your application through declarative YAML files, automatically scaling services to your desired state, load balancing across containers within the cluster, and security and access control across your services. If you have few workloads running, don’t mind managing your own infrastructure, or don’t need a specific feature Kubernetes offers, then Docker Swarm may be a great choice.

Kubernetes is more complex to set up in the beginning but offers greater flexibility and features. It also has wide support from an active open source community. Kubernetes supports multiple deployment strategies out of the box, can manage your network ingress, and provides observability out of the box into your containers. All major cloud vendors offer managed Kubernetes services that make it significantly easier to get started and take advantage of cloud native features, like auto-scaling. If you are running many workloads and require cloud native interoperability, and have many teams in your organization, which creates the need for greater isolation of services, then Kubernetes is likely the platform you should consider.

# Kubernetes benefits


Kubernetes, often described as the “Linux of the cloud” is the most popular container orchestration platform for a reason. Here are some of the reasons why:

### Automated operations

Kubernetes comes with a powerful API and command line tool, called kubectl, which handles a bulk of the heavy lifting that goes into container management by allowing you to automate your operations. The controller pattern in Kubernetes ensures applications/containers run exactly as specified.

### Infrastructure abstraction

Kubernetes manages the resources made available to it on your behalf. This frees developers to focus on writing application code and not the underlying compute, networking, or storage infrastructure.

### Service health monitoring

Kubernetes monitors the running environment and compares it against the desired state. It performs automated health checks on services and restarts containers that have failed or stopped. Kubernetes only makes services available when they are running and ready.

