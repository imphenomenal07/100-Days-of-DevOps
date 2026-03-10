# Day 40: Docker EXEC Operations

# 1. Login into server
  $  ssh user@host

# 2. Check status of Docker service
  $  systemctl status docker

# 3. Check running conatiners and images
  $  docker ps; docker images

# 4. Now install apache2 service using 'apt'
  $  docker exec -it kkloud apt install apache2 -y

# 5. Configuring apache2 port at 6100
  $  docker exec -it kkloud sed -i 's/Listen 80/Listen 6100/' /etc/apache2/ports.conf

# 6. Update default virtual host
  $  docker exec -it kkloud sed -i 's/<VirtualHost \*:80>/<VirtualHost *:6100>/' /etc/apache2/sites-available/000-default.conf

# 7. Now restart service
  $  docker exec -it kkloud service apache2 restart

# 8. Check status of service
  $  docker exec -it kkloud service apache2 status

# 9. Verify if service listening on port 6100
  $  docker exec -it kkloud apachectl -S

# 10. To verify if service is active and running
#Open new terminal and curl the service

  $  curl localhost:6100
  $  curl containerIP:6100
