# Kubernetes Cluster Launch


**Author:** Mohamed Mohamed  
**Email:** mohamed0395@gmail.com

---

![Image](https://i.imgur.com/KtPaM7O.png)

---

## Kubernetes Project

In this project, I will be deploying a Kubernetes cluster, because it automates deployment, scaling and management of containerized applications, ensuring high availability, resource efficiency, and seamless portability across cloud environments.

### What is Amazon EKS?

Amazon EKS is a managed Kubernetes service for running containerized apps. In today’s project, I used it to create a cluster and set up a node group, ensuring my apps run on managed EC2 instances with automated scaling and orchestration. I didn’t expect the cluster creation process to take so long. It made me realize the importance of automation or templates to speed up future deployments. This project took me a few hours and the longest part was deploying this clusters and nodes.

---

## What is Kubernetes?

Kubernetes is a container orchestration platform, which is a fancy way to say that it coordinates containers so they're running smoothly across all your servers. Companies and developers use Kubernetes to simplify the management of the environment.

I used eksctl to create and manage Amazon EKS clusters. The create cluster command I ran defined the cluster’s name, region, and node configuration, making it easy to set up and deploy Kubernetes on AWS.

I initially ran into two errors while using eksctl. The first one was because I hadn’t installed eksctl on my system. The second one was because I didn’t have the right IAM role and permissions for the EC2 instance, preventing it from managing EKS.

![Image](https://imgur.com/9e2Ei03.png)

---

## eksctl and CloudFormation

CloudFormation helped create my EKS cluster because eksctl uses it to provision and manage resources. It created VPC resources because the cluster needed networking, subnets, and security groups for proper communication and operation.

There was also a second CloudFormation stack for my node group, which is a group of EC2 instances that will run my containers. The difference between a cluster and node group is, a cluster hosts workloads, while a node group manages worker nodes.

![Image](https://i.imgur.com/bz1XTVp.png)

---

## The EKS console

I had to create an IAM access entry in order to communicate with services like EKS to create a cluster. An access entry is a rule for permissions. I set it up by defining users, roles, and access levels in the system.

It took 10 minutes to create my cluster. Maybe this process could be sped up if I use a automation script.

![Image](https://i.imgur.com/KtPaM7O.png)

---

## EXTRA: Deleting nodes

Did you know you can find your EKS cluster's nodes in Amazon EC2? This is because EKS worker nodes are actually EC2 instances managed by node groups.

Desired size is the target number of nodes in your node group. Minimum and maximum sizes are helpful for maintaining availability during low demand and scaling up during high demand.

When I deleted my EC2 instances, my EKS cluster replaced them with new ones. This is because the node group ensures the desired number of nodes is maintained, unless I delete in cloudformation.

![Image](https://i.imgur.com/tXZlNUe.png)

---

---
