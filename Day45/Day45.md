# Day 45: Resolve Dockerfile Issues

# 1. Login into server
  $  ssh user@host

# 2. Check status of docker service
  $  systemctl status docker

# 3. Go to working repo
  $  cd /opt/docker

# 4. Check the content of Dockerfile
  $  cat Dockerfile

# 5. Now try to build the docker image with the same dockerfile
  $  docker build -t test-image .

#If any error comes, make sure COPYING path should be correct for certs and index file.
#Update the paths and re-build docker image, if there is any other image with same build, remove that first.

# 6. To verify, you we can also run docker container with the same image
  $  docker run -d --name container-name -p 8080:80 image:tag
