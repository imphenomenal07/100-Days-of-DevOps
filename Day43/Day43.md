# Day43: Docker Ports Mapping

# 1. Login into server
  $  ssh user@host

# 2. Check status of docker service
  $  systemctl status docker

# 3. Now pull the docker image
  $  docker pull nginx:stable

# 4. Check the available docker images
  $  docker images #you will be nginx docker image

# 5. Now create and run docker container with the port mapping, host port - 6000 and container port - 80
  $  docker run -d --name beta -p 6000:80 nginx:stable
#docker run -d --name container-name -p host-port:container-port image-name:tag

# 6. Check if the running docker container
  $  docker ps
