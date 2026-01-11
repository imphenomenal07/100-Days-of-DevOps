# Day 51: Execute Rolling Updates in Kubernetes

# 1. Check if there is any running deployment
  $  kubectl get deployment

# 2. Check the runing pods
  $  kubectl get pods

# 3. Now update the deployment image
  $  kubectl set image deployment/nginx-deployment nginx-container=nginx:1.18

#kubectl set image deployment/deployment-name container-name=image:tag

# 4. Check the status of rolling update
  $  kubectl rollout status deployment/nginx-deployment

# 5. Check the running pods after roll out
  $  kubectl get pods

# 5. Check the image, if updated or not
  $  kubectl describe deployment nginx-deployment | grep -i image
