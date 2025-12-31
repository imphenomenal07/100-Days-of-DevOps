# Day26: Git Manage Remotes

# 1. Login into the server
  $ ssh user@host

# 2. Go to the repo
  $ cd /usr/src/kodekloudrepos/games

# 3. Add the new remote repo
  $ sudo git remote add dev_games /opt/xfusioncorp_games.git

# 4. Check if new remote repo added or not
  $ sudo git remove -v

# 5. Now copy index file to current repo
  $ sudo scp /tmp/index.html .

# 6. Confirm you are master branch
  $ sudo git checkout master

# 7. Now add the index file and commit
  $ sudo git add index.html
  $ sudo git commit -m "commit message"

# 8. Now push master branch to new remote
  $ sudo git push dev_games master

After this, master branch will be updated to remote branch
