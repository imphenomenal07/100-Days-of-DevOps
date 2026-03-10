# Day 48: Deploy Pods in Kubernetes Cluster

# 1. To deploy pod, create a YAML file with give configurations
  $  vi pod.yaml

#apiVersion: v1
kind: Pod
metadata:
  name: pod-name
  labels:
    app: app-label
spec:
  containers:
    - name: container-name
      image: image-name:tag
      ports:
        - containerPort: port-no.

#Save and exit from the file

# 2. Now create pods with the file
  $  kubectl apply -f pod.yaml

# 3. Get the running pods
  $ kubectl get pods

#Pod should be running
