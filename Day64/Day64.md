# Day 64: Fix Python App Deployed on Kubernetes Cluster

# 1. First check status of deployment, pods and service
  $  kubectl get deployment; kubectl get pods; kubectl get svc

#From here, you will understand what is issue.

# 2. Create yaml file for running deployment
  $  kubectl get deployment deployment-name -o yaml > deployment.yaml

# 3. Now delete the current deployment
  $  kubectl delete deployment deployment-name

#Troubleshoot shoot the issue, there is typo in docker image. Update that and run the deployment again.
  $  kubectl apply -f deployment.yaml

# 4. Create yaml file for running service
  $  kubectl get get svc service-name -o yaml > service.yaml

# 5. Delete the current service
  $  kubectl delete svc service-name

#Troubleshoot the service issue, there is target port mismatch in serice. Update the target port and create the service again.
  $  kubectl apply -f service.yaml
