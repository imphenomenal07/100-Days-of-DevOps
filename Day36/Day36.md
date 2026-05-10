# Day 36: Deploy Nginx Container on Application Server

# 1. Login into server and switch to root user
  $  ssh user@host
  $  sudo -i

# 2. Check status of docker, it is running or not
  $  systemctl status docker

#If not running, restart the docker service

# 3. Now pull the image with 'alpine' tag
  $  docker pull nginx:alpine

# 4. Create and run the container
  $  docekr run -d --name nginx_1 -p 80:80 nginx:alpine

# 5. Verify the container is running or not
  $  docker ps

# OR <For extra verification>
$  docker inspect -f '{{.State.Status}}' nginx_1
