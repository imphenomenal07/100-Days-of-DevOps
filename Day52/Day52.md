# Day 52: Revert Deployment to Previous Version in Kubernetes

# 1. Check status of running pods
  $  kubectl get pods

# 2. Check rollout histroy
  $  kubectl rollout history deployment/deployment-name

# 3. Now rollback to previous version
  $  kubectl rollout undo deployment/nginx-deployment --to-revision=1

# 4. Check again running pods and rollout history
  $  kubectl get pods; kubectl rollout history deployment/nginx-deployment
