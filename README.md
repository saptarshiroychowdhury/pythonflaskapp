🚀 CI/CD Pipeline for Dockerized Flask App using Jenkins & Kubernetes (Minikube)

This project demonstrates a complete CI/CD pipeline for deploying a Dockerized Python Flask application to a Kubernetes (Minikube) cluster using Jenkins.

The pipeline automatically:

Fetches the latest code from GitHub

Builds a Docker image

Pushes the image to Docker Hub

Deploys the updated app to Minikube using Kubernetes manifests

🧰 Tech Stack
Tool	Purpose
Python Flask	Web application
Docker	Containerization
Docker Hub	Container registry
Jenkins	CI/CD automation
Kubernetes (Minikube)	Deployment environment
Git & GitHub	Version control & repo hosting
📂 Project Structure
pythonflaskapp/
│
├── app.py                # Flask application
├── requirements.txt      # Dependencies
├── Dockerfile            # Build container image
├── deployment.yaml       # Kubernetes Deployment
├── service.yaml          # Kubernetes Service
└── Jenkinsfile           # CI/CD pipeline script

⚙️ Pipeline Workflow
🔹 1. Fetch Code

Jenkins clones the GitHub repository:

git clone https://github.com/saptarshiroychowdhury/pythonflaskapp.git

🔹 2. Build Docker Image

Jenkins builds the image using the Dockerfile:

docker build -t saptarshi500/flaskapp:latest .

🔹 3. Push to Docker Hub

Image is pushed to your Docker Hub repository:

docker push saptarshi500/flaskapp:latest


Jenkins uses a stored credential (dockerhub) for login.

🔹 4. Deploy to Kubernetes (Minikube)

Jenkins applies the Kubernetes manifests:

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml


This updates the running application with the newly pushed image.

🧪 How to Run Locally
1️⃣ Clone the Repository
git clone https://github.com/saptarshiroychowdhury/pythonflaskapp.git
cd pythonflaskapp

2️⃣ (Optional) Test Locally with Docker
docker build -t flaskapp .
docker run -p 5000:5000 flaskapp

🚀 Deploy Manually (If Needed)
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

Check running pods:
kubectl get pods

Access the app:
minikube service pythonflask

🛠️ Jenkins Setup
1. Install Required Plugins

Docker Pipeline

Kubernetes CLI

Git

2. Add Credentials

Docker Hub username/password → ID: dockerhub

3. Create a Pipeline Job

Use the provided Jenkinsfile in the repo.

📌 What This Project Demonstrates

✔️ Full CI/CD pipeline
✔️ Automated Docker image build & push
✔️ Automated Kubernetes deployment
✔️ Clean folder-based application structure
✔️ Practical DevOps skills (Docker + Jenkins + K8s)
