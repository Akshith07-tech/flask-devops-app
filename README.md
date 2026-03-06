# Flask DevOps CI/CD Project 🚀

This project demonstrates a **simple DevOps CI/CD pipeline** that deploys a Flask application to **Kubernetes (Minikube) running on an AWS EC2 instance** using **GitHub Actions**.

The goal of this project is to understand the **end-to-end DevOps workflow** including containerization, Kubernetes deployment, and automated CI/CD.

---

# Project Architecture

Developer → GitHub → GitHub Actions → EC2 Server → Docker → Minikube → Kubernetes Deployment → Service

---

# Tech Stack

* Python (Flask)
* Docker
* Kubernetes
* Minikube
* AWS EC2
* GitHub Actions
* Linux

---

# Project Structure

flask-devops-app/

* app.py
* requirements.txt
* Dockerfile
* k8s/
   * deployment.yaml
   * service.yaml
* .github/workflows/ci-cd.yml

---

# Step 1 – Clone Repository

git clone https://github.com/Akshith07-tech/flask-devops-app.git

cd flask-devops-app

---

# Step 2 – Build Docker Image

docker build -t flask-devops-app:latest .

---

# Step 3 – Load Image into Minikube

minikube image load flask-devops-app:latest

---

# Step 4 – Deploy to Kubernetes

kubectl apply -f k8s/deployment.yaml

kubectl apply -f k8s/service.yaml

---

# Step 5 – Verify Deployment

Check pods

kubectl get pods

Check services

kubectl get svc

---

# Step 6 – Access the Application

Run port forwarding:

kubectl port-forward svc/flask-service 5000:5000 --address 0.0.0.0

Now open in browser:

http://EC2_PUBLIC_IP:5000

Example:

http://13.59.147.88:5000

---

# CI/CD Pipeline (GitHub Actions)

Whenever code is pushed to the **main branch**, GitHub Actions will:

1. Checkout the repository
2. SSH into the EC2 instance
3. Copy project files
4. Build Docker image
5. Load image into Minikube
6. Update Kubernetes deployment

Pipeline file:

.github/workflows/ci-cd.yml

---

# Kubernetes Components Used

Deployment
Runs Flask application containers.

Service (NodePort)
Exposes the application outside the cluster.

---

# Useful Commands

Check pods

kubectl get pods -o wide

Check services

kubectl get svc

Describe deployment

kubectl describe deployment flask-deployment

Check logs

kubectl logs <pod-name>

Delete deployment

kubectl delete deployment flask-deployment

---

# Learning Outcome

Through this project I learned:

* Docker containerization
* Kubernetes deployments
* Kubernetes services
* Minikube cluster management
* CI/CD using GitHub Actions
* Remote deployment to AWS EC2

---

# Author

Akshith

GitHub:
https://github.com/Akshith07-tech
