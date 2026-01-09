# Day42: Create a Docker Network

# 1. Login into server
  $  ssh user@host

# 2. Check status of docker service
  $  systemctl status docker

# 3. Create network with the mentioned configurations

  $  docker network create -d macvlan \
  --subnet=172.168.0.0/24 \
  --ip-range=172.168.0.0/24 \
  beta

#docker network create -d driver-name \
  --subnet=<subnet-range> \
  --ip-range=<IP-range> \
  --gateway=<Gateway-IP> \
  -o parent=eth0 \
  network-name

# 4. To check the network configuration, inspect the docker network
  $  dicker network inspect network-name
