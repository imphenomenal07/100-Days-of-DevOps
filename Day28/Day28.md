# Day28: Git Cherry Pick

# 1. Login into storage server
  $  ssh user@host

# 2. Go to the repo
  $  cd /usr/src/kodekloudrepos/blog

# 3. Check avalable branches
  $  sudo git branch

# 4. Find commit hash (commitID) on feature branch
  $  sudo git checkout master

# 5. Check commit logs and copy commitID of 'Update info.txt'
  $  sudo git log --oneline

# 6. Switch to master
  $  sudo git checkout master

# 7. Now cherry pick the commit
  $  sudo git cherry-pick <paste the commitID that copied from 'Update info.txt'>

# 8. Push changes to the remote repo
  $  sudo git push origin master
