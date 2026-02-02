# Dicecamp Clone  DevOps 101 Project

This project is a simple static website inspired by dicecamp.com, built to demonstrate a **full local DevOps workflow** using Docker, Docker Compose, Kubernetes (Minikube), GitHub, and CI/CD foundations.

The goal is to understand how an application moves from **local files â†’ container â†’ Kubernetes â†’ version control â†’ cloud deployment**.

---

##·± Project Overview

**What this project includes:**
- Static HTML/CSS website
- Docker image using NGINX
- Local development with Docker Compose
- Kubernetes deployment using Minikube
- Git version control
- GitHub Actions CI pipeline (build validation)
- Prepared for EC2 deployment

---

## Project Structure

dicecamp-clone/
├── site/
│ ├── index.html
│ └── styles.css
├── Dockerfile
├── docker-compose.yml
├── k8s/
│ ├── deployment.yaml
│ └── service.yaml
├── .github/
│ └── workflows/
│ └── ci-cd.yml
├── README.md


---

## Website

- Pure HTML and CSS
- Served using NGINX
- Files located in `site/`

---

## Docker

### Dockerfile
- Uses `nginx:alpine` as a base image
- Copies static website files into NGINX web root
- Exposes port 80

### Build image locally
```bash
docker build -t dicecamp:1.0 .

### Run container locally
docker run -p 8080:80 dicecamp:1.0

### Access at:
http://localhost:8080

### Run with Docker Compose
docker compose up --build

### Access at:
http://localhost:8080

### Start Minikube
minikube start --driver=docker

### Kubernetes manifests
### deployment.yaml - defines the app deployment
### service.yaml - exposes the app via NodePort

### Deploy to Minikube
kubectl apply -f k8s/

### Load Docker image into Minikube (Windows / Git Bash)
minikube image load dicecamp:1.0

### Access the service
minikube service dicecamp-service

### CI/CD (GitHub Actions)
Current Pipeline
Triggered on every push to main
Checks out repository
Builds Docker image to ensure project integrity
File location:
.github/workflows/ci-cd.yml

