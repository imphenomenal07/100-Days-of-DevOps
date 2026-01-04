# Day30: Git hard reset

# 1. Login into the server
  $ ssh user@host

# 2. Go the repo
  $  cd /usr/src/kodekloudrepos/media

# 3. Check branch
  $  sudo git branch


# 4. Check commit hash (commitID) for the previous commits
  $ sudo git log --oneline

# 5. Now reset the commits as mentioned in the task
  $ sudo git reset --hard commit-hash

# 5. Switch to master branch and push the changes
  $  sudo git checkout master
  $  sudo push origin master #use 'sudo git push origin master -f' if you face any errors.
