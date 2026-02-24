# 🚀 MEAN Stack DevOps Deployment with CI/CD

### A production-ready MEAN (MongoDB, Express, Angular, Node.js) application deployed using:

Docker & Docker Compose

Nginx Reverse Proxy

GitHub Actions CI/CD

Docker Hub

AWS EC2 (Ubuntu)

## 📌 Project Architecture

```
Browser
   ↓
Nginx Reverse Proxy (Port 80)
   ↓
Frontend (Angular)
   ↓
Backend (Node + Express)
   ↓
MongoDB
```
## 🛠️ Tech Stack

Frontend: Angular 15

Backend: Node.js + Express

Database: MongoDB

Containerization: Docker

Orchestration: Docker Compose

CI/CD: GitHub Actions

Container Registry: Docker Hub

Cloud Provider: AWS EC2 (Ubuntu)

Reverse Proxy: Nginx

## 📂 Project Structure

```
MEAN-APP/
│
├── backend/
│   ├── Dockerfile
│   ├── server.js
│
├── frontend/
│   ├── Dockerfile
│   ├── dist/
│
├── nginx/
│   └── default.conf
│
├── docker-compose.yml
└── .github/workflows/deploy.yml
```

## ⚙️ Step-by-Step Setup & Deployment

### 🔹 1. Clone Repository
```
git clone https://github.com/saranuu/MEAN-APP.git
cd MEAN-APP
```

### 🔹 2. install Docker 
(👉 Just copy this into a file (e.g., install-docker-ce.sh), make it executable with chmod +x install-docker-ce.sh, and run it using ./install-docker-ce.sh)
```
#!/bin/bash

# Remove docker.io if installed
sudo apt-get remove -y docker.io
sudo apt-get purge -y docker.io
sudo apt-get autoremove -y

# Update package index
sudo apt-get update

# Install prerequisites
sudo apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common

# Add Docker’s official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# Add Docker repository (replace $(lsb_release -cs) with your Ubuntu codename if needed)
sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"

# Update package index again
sudo apt-get update

# Install Docker CE
sudo apt-get install -y docker-ce docker-ce-cli containerd.io

# Verify installation
docker --version

# Optional: allow running docker without sudo
sudo usermod -aG docker $USER
echo "Log out and back in to apply docker group changes."

```

### 🔹 3. CI/CD Workflow

.github/workflows/deploy.yml

Pipeline automatically:

Builds Docker images

Pushes to Docker Hub

SSH into EC2

Pulls latest images

Restarts containers

Trigger:
```
git push origin main
```
### 🔹 4. Start Application on EC2 (First Time)
```docker compose up -d```
Application URL:
```http://YOUR_PUBLIC_IP```

## 🔄 CI/CD Workflow Overview
## 📦 Build & Push Process

### GitHub Actions triggered on push to main
1.Backend image built
2.Frontend image built
3.Images pushed to Docker Hub
4.SSH into EC2
5.Pull latest images
6.Restart containers

## ✅ CI/CD Pipeline Execution
screenshot : https://photos.app.goo.gl/BZaditGt9uPmqhCTA

Description:
🔹Successful GitHub Actions workflow
🔹Backend & frontend images built
🔹Deployment step completed

## 🐳 Docker Image Build & Push
screenshot : https://photos.app.goo.gl/HJCFnFmPioSjEozU9

Description:
🔹Images tagged
🔹Pushed to Docker Hub
🔹Latest tag updated

## 🌐 Application Deployment (Working UI)
screenshot : https://photos.app.goo.gl/XW9Yu2xNeAWn4j4R7

Description:
🔹Angular frontend loaded
🔹Backend API integrated
🔹Data fetched successfully

## 🔁 Nginx Reverse Proxy Setup
screenshot : https://photos.app.goo.gl/1499z4bEbJoALEWE8

Description:
🔹Reverse proxy configuration
🔹/api routing to backend
🔹Single public port exposed

## 🔐 Infrastructure Details
AWS EC2 Configuration
Instance Type: t2.medium
OS: Ubuntu 22.04
Security Group:
Port 80 (HTTP)
Port 22 (SSH)

## 👨‍💻 Author

Sai Saran Ruppa
DevOps & Cloud Enthusiast
