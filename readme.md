# 🚀 Start Minikube

minikube start --driver=docker

kubectl get nodes

---

# 🧪 1. Deploy Nginx Pod

## ▶️ Create Pod
kubectl run nginx-pod --image=nginx --port=80

## ▶️ Verify Pod
kubectl get pods

Expected:
nginx-pod   Running

---

## 🌐 Expose Pod
kubectl expose pod nginx-pod --type=NodePort --port=80

## ▶️ Check Service
kubectl get services

---

## 🌍 Access
minikube service nginx-pod

Expected Output:
Welcome to nginx!

---

## 🛑 Cleanup
kubectl delete pod nginx-pod
kubectl delete service nginx-pod

---

# 🧪 2. Deploy Flask App (From Docker Hub)

## ▶️ Create Deployment
kubectl create deployment flask-deploy --image=tempjava30/flask-app:latest

## ▶️ Verify Pods
kubectl get pods

Expected:
flask-deploy-xxxxx   Running

---

## ▶️ Expose Deployment
kubectl expose deployment flask-deploy --type=NodePort --port=5000

---

## 🌐 Access Application
minikube service flask-deploy

Expected Output:
Hello from Flask App

---

# 📈 3. Scale Application

## ▶️ Scale to 3 Replicas
kubectl scale deployment flask-deploy --replicas=3

## ▶️ Verify
kubectl get pods

Expected:
3 Pods Running

---

## 🛑 Cleanup(make sure to delete before flask ui app)
kubectl delete deployment flask-deploy
kubectl delete service flask-deploy

---
# 🎨 Deploy Flask UI App (Docker Hub)

## ▶️ Create Deployment

```bash
kubectl create deployment flask-ui-deploy \
  --image=tempjava30/flask-ui-app:latest

kubectl get pods

kubectl expose deployment flask-ui-deploy \
  --name=flask-ui-service \
  --type=NodePort \
  --port=5000

kubectl get services

minikube service flask-ui-service

---

# 🛑 Final Cleanup

kubectl delete deployment flask-deploy
kubectl delete service flask-deploy
