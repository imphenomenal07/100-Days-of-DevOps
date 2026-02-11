# Day 22: Clone Git Repository on Storage Server

# 1. Login into storage server
  $ ssh user@server

# 2. Initialize git repo
  $ sudo git init

# 3. Change directory to where repo needs to be cloned
  $ cd /usr/src/kodekloudrepos

# 4. Now clone git with the user
  $ sudo -u natasha git clone /opt/demo.git

In case of any issues, check permissions
