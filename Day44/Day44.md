# Day44: Write a Docker Compose File

# 1. Login into server
  $  ssh user@host

# 2. Check status of docker service
  $  systemctl status docker

# 3. Go to the working repo
  $  cd /opt/docker

# 4. Create docker compose file
  $  vi docker-compose-yml

# Add below content to file

version: "3.9"

services:

  web:
  
    image: httpd:latest
    
    container_name: httpd
    
    ports:
      - "5000:80"
      
    volumes:
      - /opt/sysops:/usr/local/apache2/htdocs

# 5. Build docker image
  $  docker compose up -d

# 6. Check,if docker container created or not
  $  docker ps
