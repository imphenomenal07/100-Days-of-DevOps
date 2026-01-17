# Day 60: Persistent Volumes in Kubernetes

# 1. Create a Persistent volume
  $  vi pv.yaml

#apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-devops
spec:
  storageClassName: manual
  capacity:
    storage: 5Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: /mnt/security

# 2. Create persistent volume claim
  $  vi pvc.yaml

#apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-devops
spec:
  storageClassName: manual
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 3Gi

# 3. Create pod file
  $  vi pod.yaml

#apiVersion: v1
kind: Pod
metadata:
  name: pod-devops
  labels:
    app: devops
spec:
  containers:
    - name: container-devops
      image: httpd:latest
      ports:
        - containerPort: 80
      volumeMounts:
        - name: web-storage
          mountPath: /usr/local/apache2/htdocs
  volumes:
    - name: web-storage
      persistentVolumeClaim:
        claimName: pvc-devops

# 4. Create service file
  $  vi service.yaml

#apiVersion: v1
kind: Service
metadata:
  name: web-devops
spec:
  type: NodePort
  selector:
    app: devops
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30008

# 5. Now create deployment for all the files
  $  kubectl apply -f pod.yaml; kubectl apply -f pv.yaml; kubectl apply -f pvc.yaml; kubectl apply -f service.yaml

# 6. Get all the service to check status
  $  kubectl get pods; kubectl get pv; kubectl get pvc; kubectl get svc

# Now access the website from top right corner!!
