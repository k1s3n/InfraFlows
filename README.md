# InfraFlow

## Overview

This repository contains a complete CI/CD pipeline for building, pushing, and deploying an Nginx-based Docker image to a Kubernetes cluster using GitHub Actions, GitHub Container Registry (GHCR), and Ansible.

## Setup and Usagge

### Prerequisites

Ensure you have the following installed:

* Docker

* Minikube

* kubectl

* Ansible

### 1. Clone repo

```bash
git clone git@github.com:k1s3n/infraflows.git
cd infraflows
```

### 2. Deploy to Kubernetes

```bash
kubectl apply -f nginx-deployment.yml
```

### 3. Start service with minikube

```bash
minikube service nginx-service
```

### 4. Run Ansible Playbook for Deployment

The kubernetes.core Ansible collection relies on Python scripts. Therefore, you need to ensure that both pip and the Kubernetes Python SDK are installed before running the Ansible playbook.

#### Step 1: Install Required Dependencies

First, install pip and the kubernetes Python package:

```bash
sudo apt install python3-pip

pip install kubernetes
```

#### Step 2: Install the kubernetes.core Ansible Collection

Once dependencies are installed, you need to install the kubernetes.core collection for Ansible:

```bash
ansible-galaxy collection install kubernetes.core
```

#### Step 3: Run the Ansible Playbook

Now, you can run the Ansible playbook to deploy your application:

```bash
ansible-playbook deploy-playbook.yml
```

#### Extra: Using Environment Variables (optional)

By default, the playbook uses these values:

* IMAGE_TAG = v1.0.1
* IMAGE_NAME = html-nginx
* DEPLOYMENT_NAME = nginx-deployment

If you need to override them, export new values before running the playbook:
```bash
export IMAGE_TAG=v1.0.3  # Change to a different version
export IMAGE_NAME=my-custom-nginx
export DEPLOYMENT_NAME=my-deployment
```
