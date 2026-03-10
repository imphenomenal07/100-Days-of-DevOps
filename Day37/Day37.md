# Day 37: Copy File to Docker Container

# 1. Login into the server
  $  ssh user@host

# 2. Check if docker is enabled and running
  $  sudo systemctl status docker

# 3. Now copy the file required location
  $  sudo docker cp /path/file.txt container_name_or_id:/path/

#sudo docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/opt/

# 4. Verify if file copied or not
  $  sudo docker exec ubuntu_latest ls -l /opt/nautilus.txt.gpg
