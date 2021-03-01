# capstone-devops

In this project, I demonstrate how to create a pipeline in Jenkins which lints a Dockerfile, creates a container of a Redis server and pushes it to DockerHub.

In addition, through an Ansible playbook, the pipeline deploys a EKS Cluster on AWS. After the creation, we deploy the image with continouus deployment.

## Requirements

In order for the pipeline to work, the user needs to install hadolint, the aws cli, docker and kubectl on the instance that runs the Jenkins server.

## Disclaimer

This repo was created as part of the Udacity Cloud DevOps Nanodegree to demonstrate the knowledge on these tools
