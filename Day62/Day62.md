# Day 62: Manage Secrets in Kubernetes

# 1. Create a genric secret with the given name
  $  kubectl create secret generic ecommerce --from-file=/opt/ecommerce.txt

# 2. Check if secret created or not
  $  kubectl get secret

# 3. Create pod file with the given details
  $  vi pod.yaml

#apiVersion: v1
kind: Pod
metadata:
  name: secret-nautilus
spec:
  containers:
    - name: secret-container-nautilus
      image: ubuntu:latest
      command:
        - sleep
        - "3600"
      volumeMounts:
        - name: secret-volume
          mountPath: /opt/demo
  volumes:
    - name: secret-volume
      secret:
        secretName: ecommerce

# 4. Create pod with the file
  $  jubectl apply -f pod.yaml

# 5. To verify, exec into container
  $  kubectl exec -it secret-nautilus -c secret-container-nautilus  -- cat /opt/demo/ecommerce.txt
