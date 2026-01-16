# Day 59: Troubleshoot Deployment issues in Kubernetes

# 1. Get the running pods
  $  kubectl get pods

# 2. Get the running deployment
  $  kubectl get deployment

# 3. Desrcibe deployment to find the issue
  $  kubectl desrcibe deployment deployment-name

#Here you you will see 2 typing mistakes: 1) Container Image typo. 2) Config map type in volume resource

# 4. Create deployment file for the current deployment
  $  kubectl get deployment deployment-name -n namespace -o yaml > deployment.yaml

# 5. Now delete the curent running deployment
  $  kubectl delete deployment deployment-name

# 6. Edit deployemnt file to fix the issue
  $  vi deployment.yaml #Make changes, save and exit from file.

# 7. Now apply to deployment to create pods
  $  kubectl apply -f deployment.yaml

# 8. Check status of deployment and pods, if they are in running state
  $  kubectl get deployment; kubectl get pods
