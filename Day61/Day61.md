# Day 61: Init Containers in Kubernetes

# 1. Create a deployment file for the given configurations
  $  vi deployment.yaml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: ic-deploy-devops
spec:
  replicas: 1
  selector:
    matchLabels:
      app: ic-devops
  template:
    metadata:
      labels:
        app: ic-devops
    spec:
      volumes:
      - name: ic-volume-devops
        emptyDir: {}

      containers:
        - name: ic-main-devops
          image: ubuntu:latest
          command: ['/bin/bash', '-c', 'while true; do cat /ic/media; sleep 5; done']
          volumeMounts:
          - name: ic-volume-devops
            mountPath: /ic
      initContainers:
        - name: ic-msg-devops
          image: ubuntu:latest
          command: ['/bin/bash', '-c',  'echo Init Done - Welcome to xFusionCorp Industries > /ic/media']
          volumeMounts:
          - name: ic-volume-devops
            mountPath: /ic

# 2. Now create deployment
  $  kubectl apply -f deployment.yaml
