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
kubectl create deployment flask-deploy --image=yourusername/flask-docker-app:latest

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

## 🛑 Cleanup
kubectl delete deployment flask-deploy
kubectl delete service flask-deploy

---

# 🎨 4. Deploy CSS Styled Flask App (Docker Hub)

## ▶️ Build Docker Image
docker build -t flask-docker-app .

---

## ▶️ Tag Image
docker tag flask-docker-app yourusername/flask-docker-app:latest

---

## ▶️ Login to Docker Hub
docker login

---

## ▶️ Push Image
docker push yourusername/flask-docker-app:latest

---

## ▶️ Deploy on Kubernetes
kubectl create deployment flask-deploy --image=yourusername/flask-docker-app:latest

---

## ▶️ Verify Pods
kubectl get pods

---

## ▶️ Expose Application
kubectl expose deployment flask-deploy --type=NodePort --port=5000

---

## 🌐 Access Application
minikube service flask-deploy

Expected Output:
Styled Flask page (black background, green text)

---

# 📈 Scale Again (Optional)

kubectl scale deployment flask-deploy --replicas=3
kubectl get pods

---

# 🛑 Final Cleanup

kubectl delete deployment flask-deploy
kubectl delete service flask-deploy