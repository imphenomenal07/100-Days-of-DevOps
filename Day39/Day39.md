# Day 39: Create a Docker Image From Container

# 1. Login into server
  $  ssh user@host

# 2. Check docker status
  $  sudo systemctl status docker
  
  #It should be enabled and running

# 3. Create Docker image from container
  $  sudo docker commit container-NAME/ID image-NAME:tag

# 4. Verify docker container and image
  $  docker ps; docker images
