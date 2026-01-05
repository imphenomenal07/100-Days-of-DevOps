# Day32: Git Rebase

# 1. Login into the server
  $  ssh user@host

# 2. Go to the repo
  $  cd /usr/src/kodekloudrepos/official

# 3. Check git branches
  $  sudo git branch

# 4. Make sure you are in feature branch
  $  sudo git checkout feature

# 5. Check git status and fetch updates before doing rebase
  $  sudo git status
  $  sudo git fetch origin

# 6. Now rebase feature on the master
  $  sudo git rebase master

# 7. Now push changes to feature branch
  $  sudo git push origin feature
  #If you face any issue while pushing changes to feature branch, then forcefully push to feature branch "sudo git push origin feature -f"
