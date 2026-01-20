# Day 66: Deploy MySQL on Kubernetes

# 1. Create a config map file
$  vi configmap.yaml

apiVersion: v1
kind: ConfigMap
metadata:
  name: my-redis-config
data:
  redis-config: |
    maxmemory 2mb

# 2. Create a deployment file
$  vi deployment.yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: redis-deployment
spec:
  replicas: 1
  selector:
    matchLabels:
      app: redis
  template:
    metadata:
      labels:
        app: redis
    spec:
      containers:
      - name: redis-container
        image: redis:alpine
        command: ["redis-server", "/redis-master/redis-config"]
        ports:
        - containerPort: 6379
        resources:
          requests:
            cpu: "1"
        volumeMounts:
        - name: data
          mountPath: /redis-master-data
        - name: redis-config
          mountPath: /redis-master
      volumes:
      - name: data
        emptyDir: {}
      - name: redis-config
        configMap:
          name: my-redis-config


# 3. Apply config map to create
$  kubectl apply -f configmap.yaml

# 4. Apply deployment to create
$  kubectl apply -f deployment.yaml

# 5. Check status of configmap, deployment and pods
$  kubectl get cm
$  kubectl get deployment
$  kubectl get pods
