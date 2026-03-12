# Day 25: Git Merge Branches

# 1. Login into storage server
  $ ssh user@server

# 2. Chnage from home to cloned repo
  $ cd /usr/src/kodekloudrepos/blog

# 3. Ensure to be in master branch and update it
  $ sudo git checkout master
  $ sudo git pull origin master

# 4. Create new branch 'nautilus' as given in task
  $ sudo git checkout -b nautilus

# 5. Copies index file to current repo
  $ sudo scp /tmp/index.html .

# 6. Now add and commit index file
  $ sudo git add . OR $ sudo git add index.html
  $ sudo git commit -m "commit message"

# 7. Switch back to master and merge the new branch
  $ sudo git checkout master
  $ sudo git merge nautilus

# 8. Push both branches into origin
  $ sudo git push origin master
  $ sudo git push origin nautilus
