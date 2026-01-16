# Day 58: Deploy Grafana on Kubernetes Cluster

# 1. Create deployment file
  $  vi deployment.yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: grafana-deployment-datacenter
spec:
  replicas: 1
  selector:
    matchLabels:
      app: grafana
  template:
    metadata:
      labels:
        app: grafana
    spec:
      containers:
        - name: grafana
          image: grafana/grafana:latest
          ports:
            - containerPort: 3000


# 2. Create service file
  $  vi service.yaml

apiVersion: v1
kind: Service
metadata:
  name: grafana-service
spec:
  type: NodePort
  selector:
    app: grafana
  ports:
    - port: 3000
      targetPort: 3000
      nodePort: 32000

# 3. Now create deployment and service
  $  kubectl apply -f deployment.yaml; kubectl apply -f service.yaml

# 4. Check status of pod
  $  kubectl get pods

# 5. Check status of service
  $  kubectl get svc

# 6. Login into Grafana UI with default user and passwrod
#user: admin
#password: admin

