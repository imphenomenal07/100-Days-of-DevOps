# Day35: Install Docker Packages and Start Docker Service

# 1. Login into the server and switch to root user
  $  ssh user@host
$  sudo -i

# 2. check OS distribution to install Docker
  $  cat /etc/os-release

# 3. Add official Docker CE repo
  $  sudo dnf config-manager \
  --add-repo \
  https://download.docker.com/linux/centos/docker-ce.repo

# 4. Install Docker CE and Docker Compose
  $  sudo dnf install -y \
  docker-ce \
  docker-ce-cli \
  containerd.io \
  docker-buildx-plugin \
  docker-compose-plugin

# 5. Start-enable docker and check status
  $  sudo systemctl enable --now docker; systemctl status docker

# 6. Add user to docker group
  $  sudo usermod -aG docker $USER; newgrp docker

# 7. Now Test
  $  docker run hello world
