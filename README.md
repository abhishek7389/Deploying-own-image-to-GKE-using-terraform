# Deploying-own-image-to-GKE-using-terraform

This repo will help you to deploy your own container image to google kubernetes engine(GKE) using terraform. I used my own docker hub  [public image](https://hub.docker.com/r/abhishek7389/trailapp) for this repo.

This repo contains several terraform configuration files.

## [gke.tf](https://github.com/abhishek7389/Deploying-own-image-to-GKE-using-terraform/gke.tf) 
This terraform file is used to configure google kubernetes engine cluster, node pools in that cluster, their machine type, scopes etc. you can change it according to your requirement.

## [kubernetes.tf](https://github.com/abhishek7389/Deploying-own-image-to-GKE-using-terraform/kubernetes.tf)
This is the file, where we configure our docker container image, firstly it takes information about your existing deployed cluster & create a deployment to deploy your container image, for kubernetes service I used NodePort to expose image. you can change it according to your kubernetes configuration file(yaml).

## [vpc.tf](https://github.com/abhishek7389/Deploying-own-image-to-GKE-using-terraform/vpc.tf)
This terraform file is used to create a new virtual private cloud network so you don't worry about your existing personal network, also you can change it to use you existing network.

## [versions.tf](https://github.com/abhishek7389/Deploying-own-image-to-GKE-using-terraform/versions.tf)
Basically, this is a file which defines provider and terraform version you used to deploy your infrastructure. I suggest go with latest one but here in this repo I used older one which is terraform 0.12. If you're using cloud shell than this version is already installed in your machine.

## [output.tf](https://github.com/abhishek7389/Deploying-own-image-to-GKE-using-terraform/output.tf)
This file is used to show your deployment details after deployment.

## [terraform.tfvars](https://github.com/abhishek7389/Deploying-own-image-to-GKE-using-terraform/terraform.tfvars)
This file is used to setup your project ID & region where you want to deploy.

## [kubernetes-dashboard-admin.rbac.yaml](https://github.com/abhishek7389/Deploying-own-image-to-GKE-using-terraform/kubernetes-dashboard-admin.rbac.yaml)
This is kubernetes dashboard configuration file for api calls & management of cluster.

# Requirements
- a GCP account
- a configured gcloud SDK
- kubectl
- terraform


# Set up

1. clone the repo into your machine 

- $git clone https://github.com/abhishek7389/Deploying-own-image-to-GKE-using-terraform

2. Change the directory where all files are located

- $cd Deploying-own-image-to-GKE-using-terraform

3. see the all configuration files & if required change it accordingly.

4. Now, initiaze the terraform in this folder & check all things are working well.
Note : I'm using terraform version 0.12 but if you're using latest version 0.15 then change required version to your version.

- $terraform init

- $terraform plan

5. If you don't get any error then let's deploy our configuration

- $terraform apply

6. After experimenting with this demo, let's clean up & destroy what we deployed.



This repo is a created with reference to the [Provision a GKE Cluster learn guide](https://learn.hashicorp.com/terraform/kubernetes/provision-gke-cluster), containing Terraform configuration files to provision an GKE cluster on GCP.
