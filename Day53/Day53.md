# Day 53: Resolve VolumeMounts Issue in Kubernetes

# 1. Check status of running pods
  $  kubectl get pods

# 2. Get the pod yaml config file
  $  kubectl get pod nginx-phpfpm -o yaml > nginx-phpfpm.yml

# 3. Fix the volume mount issue
  $  vi nginx-phpfpm.yml

#Now make sure both the VolumeMount and MountPath should be same.
#To make sure the correct path, check config map file.

$  kubectl get cm nginx-config -o yaml
OR
$  kubectl edit configmap nginx-config

# Once Path issue is fixed, save and exit from file.

# 5. First delete the old pods
  $ kubectl delete pod nginx-phpfpm

# 6. Now create new one
  $  kubectl appy -f nginx-phpfpm.yml

# 7. Copy index file to container
  $  kubectl cp /home/thor/index.php nginx-phpfpm:/var/www/html/index.php -c nginx-container

# Now access the website by clciking on top right corner at website icon.
