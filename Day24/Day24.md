# Day24: Git Create Branches

# 1. Login into the storage server
  $ ssh user@server

# 2. Change from home directory to working directory
  $ cd /usr/src/kodekloudrepos/apps

# 3. Make sure you are on master branch
  $ sudo git check out master

# 4. Update the master branch
  $ sudo git pull origin master

# 5. Create and switch to new branch
  $ sudo git checkout -b branch-name

# 5. Now verify the git branches
  $ sudo git branch
