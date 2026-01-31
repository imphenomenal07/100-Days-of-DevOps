# Day 21: Set Up Git Repository on Storage Server

# 1. Login into the storage server
  $ ssh user@server

# 2. Install git
  $ sudo yum install git -y

# 3. Create bare repo on the given location

  $ sudo git init --bare /opt/apps.git

# 4. ChecK out
  $ ls /opt/apps.git

  Output:

  HEAD  config  hooks  objects  refs

If you do not see output like this, troubleshoot and do 'git init' again.
