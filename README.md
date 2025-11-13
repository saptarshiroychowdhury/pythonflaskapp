# 🚀 Flask App Continuous Deployment using Jenkins and Kubernetes

🧭 Project Overview

This project demonstrates Continuous Deployment (CD) using Jenkins to automate the deployment of a pre-built Dockerized Flask application
onto a Kubernetes (Minikube) cluster.The Docker image of the Flask app was built and pushed manually to Docker Hub, and Jenkins was 
configured to automatically pull the latest Kubernetes manifests from GitHub and deploy them to the cluster.

| Tool                      | Purpose                                  |
| ------------------------- | ---------------------------------------- |
| **Python Flask**          | Application framework                    |
| **Docker**                | Containerization of the Flask app        |
| **Docker Hub**            | Image registry (manually uploaded image) |
| **Kubernetes (Minikube)** | Container orchestration                  |
| **Jenkins**               | Continuous Deployment automation         |
| **Git & GitHub**          | Version control and manifest storage     |


⚙️ Pipeline Workflow
1)Code Fetch
Jenkins pulls the latest Kubernetes YAMLs and code from GitHub.

2)Deployment Stage
Jenkins applies the manifests using kubectl to deploy the pre-built image from Docker Hub to Minikube.

3)Verification
Once deployed, the Flask app runs on Kubernetes and is exposed via a NodePort service.


🗂️ Project Structure
pythonflaskapp/
│
├── app.py                # Flask application code
├── requirements.txt      # Python dependencies
├── Dockerfile            # Used earlier for manual image build
├── deployment.yaml       # Kubernetes Deployment manifest
├── service.yaml          # Kubernetes Service manifest
└── Jenkinsfile           # CD pipeline definition

🧪 How to Run
1️⃣ Clone the Repo
git clone https://github.com/saptarshiroychowdhury/pythonflaskapp.git
cd pythonflaskapp

2️⃣ (Optional) Verify the Image
docker pull saptarshi500/flaskapp:latest

3️⃣ Apply Manifests Manually (to test)
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

4️⃣ Jenkins Deployment

Create a new Jenkins pipeline.

Paste the contents of the Jenkinsfile.

Run the pipeline — Jenkins will automatically:

Fetch the repository

Apply deployment.yaml and service.yaml using kubectl

✅ Verify Deployment
kubectl get pods
kubectl get svc
minikube service pythonflask
