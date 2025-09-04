# Node.js App with Docker & Kubernetes Deployment

## 🚀 Project Overview
This project demonstrates how to:
- Build a simple Node.js app
- Containerize it using Docker
- Push the image to DockerHub
- Deploy it on Kubernetes using `kubectl` commands
- Update the app using Kubernetes Rollout

---

## 🛠 Steps

```bash
# 1. Build Docker Image
docker build -t <dockerhub-username>/my-webapp:v1 .

# 2. Push to DockerHub
docker login
docker push <dockerhub-username>/my-webapp:v1

# 3. Deploy to Kubernetes
kubectl create deployment my-webapp --image=<dockerhub-username>/my-webapp:v1
kubectl get deployments
kubectl get pods

# 4. Expose the App
kubectl expose deployment my-webapp --type=NodePort --port=3000 --target-port=3000

# 5. Access the App (on Minikube)
minikube service my-webapp

# 6. Push new version to DockerHub
docker build -t <dockerhub-username>/my-webapp:v2 .
docker push <dockerhub-username>/my-webapp:v2

# 7. Update deployment image (Rollout)
kubectl set image deployment/my-webapp my-webapp=<dockerhub-username>/my-webapp:v2
