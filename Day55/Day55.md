# Day 55: Kubernetes Sidecar Containers

Official doc: https://kubernetes.io/docs/concepts/workloads/pods/sidecar-containers/

# 1. Create a yaml file to create pods with the mentioned specifications
  $  vi pod.yml

apiVersion: v1
kind: Pod
metadata:
  name: webserver
spec:
  volumes:
    - name: shared-logs
      emptyDir: {}

  containers:
    - name: nginx-container
      image: nginx:latest
      volumeMounts:
        - name: shared-logs
          mountPath: /var/log/nginx

    - name: sidecar-container
      image: ubuntu:latest
      command:
        - sh
        - -c
        - |
          while true; do
            cat /var/log/nginx/access.log /var/log/nginx/error.log;
            sleep 30;
          done
      volumeMounts:
        - name: shared-logs
          mountPath: /var/log/nginx


# 2. Create pods with the yaml file
  $  kubectl apply -f pod.yml

# 3. Check the pods are created and running
  $  kubectl get pods

#Pods should be created and in running state. If they are not running, wait for 10-15 secs then check again.
