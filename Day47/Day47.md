# Day 47: Docker Python App

# 1. Login into server
  $  ssh user@host

# 2. Check status of docker service
  $  systemctl status docker

# 3. Go to working repo
  $  cd /python_app

# 4. Create Dockerfile
  $  vi Dockerfile

#FROM python:latest

#Set working directory
WORKDIR /app

#Copy requirements file
COPY src/requirements.txt .

#Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

#Copy application code
COPY src/server.py .

#Expose service at port 3000
EXPOSE 3000

#Run the server in foreground
CMD ["python", "server.py"]

#Then save and exit from file

# 5. Now create docker image from file
  $  docker build -it image-name:tag .

# 6. Now create docker container
  $  docker run -d --name container-name -p host-port:container-port image-name:tag

# 7. Check docker contianer and image
  $  docker ps; docker images

# 8. Open new terminal and check connectivity
  $  curl stapp01:host-port
