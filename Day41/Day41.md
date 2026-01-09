# Day41: Write a Docker File

# 1. Login into server
  $  ssh user@host

# 2. Go to the repo
  $  cd /opt/docker/

# 3. Create a Dockerfile
  $  vi Dockerfile

# 4. Start writing Dockerfile

FROM ubuntu:24:04

WORKDIR .

#Update and Install 'apache2'

RUN apt update -y && apt install -y apache2

#Configure apache2 to listen on port no. 5004

RUN sed -i 's/Listen 80/Listen 6100/' /etc/apache2/ports.conf

#Expose service at port 5004

EXPOSE 5004

#Run service in FOREGROUND mode

CMD ["apachectl", "-D", "FOREGROUND"]

# 4. Build a docker test image
  $  dicker build -t test .

# 5. Run docker container at 5004
  $  docker run -d -p 90:5004 test

# 6. To verify the connectivity, open new terminal and curl the service
  $  curl stapp02:90
