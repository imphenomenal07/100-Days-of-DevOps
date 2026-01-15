# Day 56: Deploy Nginx Web Server on Kubernetes Cluster

# 1. Create a deployment file
  $  vi Deployment.yaml

#Official doc: https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80

# 2. Create service file for NodePort
  $  vi service.yaml

#Official doc: https://kubernetes.io/docs/concepts/services-networking/service/

apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
      nodePort: 30011

# 3. Now create deployment and service
  $  kubectl apply -f Deployment.yaml; kubectl apply -f service.yaml
