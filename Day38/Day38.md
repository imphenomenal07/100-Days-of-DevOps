# Day 38: Pull Docker Image

# 1. Login into server and check status of docker service
  $  ssh user@host
$  sudo systemctl status docker #It should be enabled and running

# 2. Pull Docker image
  $  sudo docker pull image:tag

# 3. Re-tag the image as given in task
  $  sudo docker tag image:old-tag image:new-tag
