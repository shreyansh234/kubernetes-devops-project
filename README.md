# Kubernetes Deployment using Minikube

A DevOps internship project demonstrating how to containerize a web application using Docker and deploy it on a local Kubernetes cluster using Minikube and kubectl.

The application runs inside Nginx containers managed by a Kubernetes Deployment with **2 replicas** and is exposed using a **NodePort Service**.

---

## Project Overview

This project demonstrates a complete local Kubernetes deployment workflow.

The web application is first packaged into a Docker image. The Docker image is then loaded into Minikube and deployed to Kubernetes using a Deployment YAML file.

Kubernetes maintains two running Pods for the application, while a NodePort Service makes the application accessible from the browser.

### Deployment Flow

```text
HTML/CSS Web Application
        ↓
     Dockerfile
        ↓
    Docker Image
        ↓
      Minikube
        ↓
Kubernetes Deployment
        ↓
    2 Running Pods
        ↓
 NodePort Service
        ↓
 Web Application
```

---

## Technologies Used

- Docker
- Kubernetes
- Minikube
- kubectl
- Nginx
- YAML
- HTML & CSS
- NodePort Service

---

## Project Structure

```text
kubernetes-devops-project/
│
├── Documents/
│   ├── 01-kubernetes-cluster-ready.png
│   ├── 02-kubernetes-pods-running.png
│   ├── 03-kubernetes-application-running.png
│   └── 04-kubernetes-final-status.png
│
├── Dockerfile
├── deployment.yaml
├── index.html
├── service.yaml
└── README.md
```

---

## Step 1 — Start Minikube

Start the local Kubernetes cluster using Docker as the driver.

```bash
minikube start --driver=docker
```

Verify the cluster:

```bash
minikube status
```

### Minikube Cluster Running

![Minikube Cluster](Documents/01-kubernetes-cluster-ready.png)

---

## Step 2 — Build the Docker Image

Build the application image using the Dockerfile.

```bash
docker build -t kubernetes-devops-app:v2 .
```

The application uses Nginx to serve the static web page.

---

## Step 3 — Load the Image into Minikube

Because this project uses a locally built Docker image, load it into Minikube:

```bash
minikube image load kubernetes-devops-app:v2
```

Verify the image:

```bash
minikube image ls
```

---

## Step 4 — Deploy to Kubernetes

Apply the Kubernetes Deployment:

```bash
kubectl apply -f deployment.yaml
```

The Deployment maintains **2 replicas** of the application.

Verify the Deployment:

```bash
kubectl get deployments
```

Check the Pods:

```bash
kubectl get pods
```

### Kubernetes Pods Running

![Kubernetes Pods](Documents/02-kubernetes-pods-running.png)

---

## Step 5 — Create the NodePort Service

Deploy the Kubernetes Service:

```bash
kubectl apply -f service.yaml
```

Verify it:

```bash
kubectl get services
```

The application uses:

```text
Service Type : NodePort
Service Port : 80
Target Port  : 80
NodePort     : 30080
```

---

## Step 6 — Access the Application

Open the application through the Minikube Service:

```bash
minikube service kubernetes-devops-service
```

### Application Running through Kubernetes

![Application Running](Documents/03-kubernetes-application-running.png)

---

## Final Kubernetes Status

The final setup contains:

- 1 Kubernetes Deployment
- 2 application Pods
- Nginx containerized web application
- NodePort Service
- CPU and memory resource requests and limits
- Local Minikube cluster

Useful verification commands:

```bash
kubectl get deployments
kubectl get pods
kubectl get services
```

### Deployment, Pods and Service

![Final Kubernetes Status](Documents/04-kubernetes-final-status.png)

---

## Kubernetes Configuration

### Deployment

The `deployment.yaml` file defines:

- Application container
- Docker image
- 2 replicas
- Container port 80
- CPU requests and limits
- Memory requests and limits

Kubernetes automatically maintains the desired number of Pods defined by the Deployment.

### Service

The `service.yaml` file creates a NodePort Service.

It forwards traffic from:

```text
NodePort 30080
      ↓
Service Port 80
      ↓
Pod / Container Port 80
      ↓
Nginx Web Application
```

---

## What I Learned

Through this project, I gained hands-on experience with:

- Creating Docker images
- Running containerized applications
- Understanding Kubernetes Pods
- Creating Kubernetes Deployments
- Managing multiple replicas
- Writing Kubernetes YAML manifests
- Using kubectl commands
- Creating Kubernetes Services
- Exposing applications using NodePort
- Running Kubernetes locally using Minikube
- Configuring basic container CPU and memory resources
- Verifying and troubleshooting Kubernetes workloads

---

## Project Goal

The main goal of this project was to gain practical experience with **container orchestration and Kubernetes deployment concepts** by deploying a Dockerized application on a local Kubernetes cluster.

---

## Author

**Shreyansh Singh**
