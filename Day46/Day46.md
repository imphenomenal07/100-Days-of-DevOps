# Day 46: Deploy an App on Docker Containers

# 1. Login into server
  $  ssh user@host

# 2. Check status of docker service
  $  systemctl status docker #It should be enabled and running

# 3. Go to working repo
  $  cd /opt/dba

# 4. Create docker compose file
  $  vi docker-compose.yml #Now create docker file

#version: "3.9"

services:
  web:
    image: php:8.3-apache-bookworm
    container_name: php_blog
    ports:
      - "3003:80"
    volumes:
      - /var/www/html:/var/www/html

  db:
    image: mariadb:latest
    container_name: mysql_blog
    environment:
      MYSQL_ROOT_PASSWORD: Ir0nM@n
      MYSQL_DATABASE: database_blog
      MYSQL_USER: mysql_blog_user
      MYSQL_PASSWORD: Ir0nM@n

    ports:
      - "3306:3306"
    volumes:
      - /var/lib/mysql:/var/lib/mysql

#Save file and exit from terminal

# 5. Create docker containers and images from file
  $  docker compose up -d

# 6. Now check docker containers and images
  $  docker ps; docker images

# 7. Access the application in new termianl with curl
  $  curl stapp01:3003
