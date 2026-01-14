# Day 54: Kubernetes Shared Volumes

# 1. Create pod yaml file to create containers
  $  vi pod.yml

#apiVersion: v1
kind: Pod
metadata:
  name: volume-share-xfusion
spec:

  restartPolicy: Never

  volumes:
  - name: volume-share
    emptyDir: {}

  containers:

  - name: volume-container-xfusion-1
    image: ubuntu:latest
    command: ["sleep", "3600"]
    volumeMounts:
    - name: volume-share
      mountPath: /tmp/media

  - name: volume-container-xfusion-2
    image: ubuntu:latest
    command: ["sleep", "3600"]
    volumeMounts:
    - name: volume-share
      mountPath: /tmp/games

#OR follow the offoical k8s docs: https://kubernetes.io/docs/tasks/access-application-cluster/communicate-containers-same-pod-shared-volume/

# 2. Now the create pods
  $  kubectl apply -f pod.yml

# 3. Check status of running pods
  $  kubectl get pods

# 4. Exec or login into first container
  $  kubectl exec -it volume-share-xfusion -c volume-container-xfusion-1 -- bash

# Create test file inside container at mounted path and exit from container

$  echo "This file is shared between containers" > /tmp/media/media.txt
exit

# 5. Verify the file from second container and check content
  $  kubectl exec -it volume-share-xfusion -c volume-container-xfusion-2 -- bash

# Check file under mounted path
$  cat /tmp/games/media.txt

#And exit from container: $ exit

# Now check complete the task. If there is any issue, troubleshoot it accordingly.
