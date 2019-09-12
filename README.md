# DevOps deployment: Jenkins, Docker, Kubernetes, AWS

This projects simulates the containerization and deployment of an app the Cloud DevOps way using Kubernetes and Docker.

To complete the deployment, I completed three steps:
First, I create an AWS VPC Infrastructure

Next, I established a Kubernetes system from master to its worker nodes using AWS EKS and EC2.

Finally, I deployed the Docker containers onto the nodes.

The following section sheds light as to how the completion of these steps was accomplished.

## The Files in this Repository
[https://github.com/call900913/dend-rchristy-project5](https://github.com/call900913/dend-rchristy-project5)

### awsfile.yml
***Infrastructure as code***
I began the project by creating the necessary infrastructure on the Cloud using AWS CloudFormation.
This file is the blueprint of that infrastructure in which we will install Kubernetes and deploy the clusters.

### Jenkinsfile
***Pipeline as code***
We use the DevOps CI/CD model for the deployment of this app.
This Jenkinsfile serves as the Jenkins pipeline.

### Dockerfile
Using the DevOps model includes containerization of the app.
This is the Dockerfile used to build the image, which is done in the Jenkins pipelin à la DevOps.

### frontend.yml
***Configuration as code***
This is the file from which the Kubernetes Control Plane creates pod and deploys our containers.

### index.html
This file represents our simulated app. We can swap this file for another set of app files to deploy another app using DevOps methodology.


## App Updates
Updates for this app will be rolled out with Blue/Green Deployment: the app itself can be accessed here:
[http://testdevops.riyanchristy.net](http://testdevops.riyanchristy.net)

This domain name has a weighted routing to two Load Balancers, which represent two K8s clusters, which in turn represent the Blue and Green clusters.

During the rollout of an update release, the domain name can be easily configured to route traffic to the appropriate cluster.
