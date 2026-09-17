# ☸️ Kubernetes DevOps Project

A simple Dockerized web application deployed on a local Kubernetes cluster using **Docker, Kubernetes, Minikube, kubectl, Deployments, Pods, and NodePort Service**.

---

## 📌 Project Overview

This project demonstrates how a web application can be containerized using Docker and deployed on a Kubernetes cluster.

The application runs inside Docker containers managed by Kubernetes. Minikube is used to create the local Kubernetes cluster, while a NodePort Service is used to access the application from the browser.

---

## 🛠️ Technologies Used

- HTML
- Docker
- Kubernetes
- Minikube
- kubectl
- Nginx
- YAML
- Git
- GitHub
- VS Code

---

## 📂 Project Structure

```text
kubernetes-devops-project/
│
├── Dockerfile
├── index.html
├── deployment.yaml
├── service.yaml
├── README.md
│
└── Documents/
    └── Documents/
        ├── 01-kubernetes-cluster-ready.png
        ├── 02-kubernetes-pods-running.png
        ├── 03-kubernetes-application-running.png
        └── 04-kubernetes-final-status.png
```

---

## 🐳 Docker Containerization

The web application is packaged inside a Docker container.

The Dockerfile uses **Nginx** as the web server and copies the `index.html` file into the Nginx web directory.

This makes the application portable and allows it to run consistently inside containers.

---

## ☸️ Kubernetes Deployment

Kubernetes is used to deploy and manage the Dockerized application.

The `deployment.yaml` file defines:

- Application Deployment
- Container image
- Container port
- Number of replicas
- CPU resource requests and limits
- Memory resource requests and limits

The project uses **2 replicas**, which means Kubernetes runs two Pods of the application.

---

## 🌐 Kubernetes Service

The `service.yaml` file creates a **NodePort Service**.

The NodePort Service exposes the application outside the Kubernetes cluster so that it can be accessed from a web browser.

### Application Flow

```text
User
  ↓
Browser
  ↓
NodePort Service
  ↓
Kubernetes Deployment
  ↓
Pods
  ↓
Docker Container
  ↓
Nginx Web Server
  ↓
Web Application
```

---

## 🚀 Deployment Steps

### 1. Start Minikube

```bash
minikube start --driver=docker
```

### 2. Check Kubernetes Cluster

```bash
kubectl get nodes
```

### 3. Apply Kubernetes Deployment

```bash
kubectl apply -f deployment.yaml
```

### 4. Check Running Pods

```bash
kubectl get pods
```

### 5. Create Kubernetes Service

```bash
kubectl apply -f service.yaml
```

### 6. Check Service

```bash
kubectl get services
```

### 7. Open Application

```bash
minikube service kubernetes-devops-service
```

---

# 📸 Project Screenshots

## 1️⃣ Kubernetes Cluster Ready

The Minikube Kubernetes cluster was successfully created and the control plane was ready.

![Kubernetes Cluster Ready](Documents/Documents/01-kubernetes-cluster-ready.png)

---

## 2️⃣ Kubernetes Pods Running

The application was deployed with **2 replicas**.

Both Kubernetes Pods are running successfully with **READY 1/1** status.

![Kubernetes Pods Running](Documents/Documents/02-kubernetes-pods-running.png)

---

## 3️⃣ Application Running on Kubernetes

The Dockerized web application was successfully deployed and accessed through the Kubernetes NodePort Service.

![Kubernetes Application Running](Documents/Documents/03-kubernetes-application-running.png)

---

## 4️⃣ Final Kubernetes Deployment Status

The final status verifies that the Kubernetes Deployment, Pods, and Service are running successfully.

![Final Kubernetes Status](Documents/Documents/04-kubernetes-final-status.png)

---

## 🔄 DevOps Workflow

```text
Web Application
      ↓
Docker Image
      ↓
Kubernetes Deployment
      ↓
Replica Pods
      ↓
NodePort Service
      ↓
Application Access
```

---

## ✨ Key Features

- Dockerized web application
- Local Kubernetes cluster using Minikube
- Kubernetes Deployment
- 2 Pod replicas
- NodePort Service
- Nginx web server
- CPU and memory resource configuration
- Kubernetes YAML configuration
- Container orchestration
- Application accessible through browser

---

## 🎯 What I Learned

Through this project, I gained practical experience with:

- Creating Docker containers
- Understanding Docker images
- Creating a Kubernetes cluster using Minikube
- Deploying applications using Kubernetes
- Working with Pods and Deployments
- Running multiple replicas
- Creating Kubernetes Services
- Using NodePort to expose applications
- Writing Kubernetes YAML files
- Using kubectl commands
- Managing containerized applications

---

## 👨‍💻 Author

**Shreyansh Singh**

Computer Engineering Student  
Cloud Computing & DevOps Enthusiast

---

## 📌 Project Status

✅ Docker Image Created  
✅ Minikube Cluster Running  
✅ Kubernetes Deployment Created  
✅ 2 Pods Running  
✅ NodePort Service Created  
✅ Application Successfully Running
