# Day 31: Git Stash

# 1. Login into the server
  $  ssh user@host

# 2. Go to the repo
  $  cd /usr/src/kodekloudrepos/news

# 3. Check git status
  $  sudo git status

# 4. Make sure you are in master branch
  $  sudo git checkout master

# 5. Check list of stashes
  $  sudo git stash list

# 6. Restore the stash that mentioned in the task
  $ sudo git stash apply stash@{1}

# 7. Now add & commit file and push to master
  $  sudo git add .
  $  sudo git commit -m "commit message"
  $  sudo git push origin main
