# Day50: Set Resource Limits in Kubernetes Pods

# 1. Create pod yaml file for creating with the given resources
  $  vi pod.yaml

#apiVersion: v1
kind: Pod
metadata:
  name: pod-name
spec:
  containers:
    - name: container-name
      image: image-name:tag
      resources:
        requests:
          cpu: "--m"
          memory: "--Mi"
        limits:
          cpu: "--m"
          memory: "--Mi"

#Save and exit from file

# 2. Now create pod with the same file
  $  kubectl apply -f pod.yaml

# 3. Get the running pods
  $  kubectl get pods
