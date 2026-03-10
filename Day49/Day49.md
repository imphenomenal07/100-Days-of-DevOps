# Day 49: Deploy Applications with Kubernetes Deployments

# 1. Create a deployment file for creating pods
  $  vi deployment.yaml

#apiVersion: apps/v1
kind: Deployment
metadata:
  name: httpd
spec:
  replicas: 1
  selector:
    matchLabels:
      app: httpd
  template:
    metadata:
      labels:
        app: httpd
    spec:
      containers:
        - name: httpd
          image: httpd:latest
          ports:
            - containerPort: 80

#Save and exit from file

# 2. Apply deployment
  $  kubectl apply -f deployment.yaml

# 3. Get runnig pods
  $  kubectl get pods

# 4. Get and describe deployment
  $  kubectl get deployment; kubectl describe deployment deployment-name
