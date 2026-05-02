# Day 34: Git Hook

# 1. Login into user
  $  ssh user@host

# 2. Go to the working repo
  $  cd /usr/src/kodekloudrepos/ecommerce

# 3. Merge 'feature' branch into 'master'
  $  sudo git checkout master; sudo git merge feature

# 4. Add the files and make commit
  $  sudo git add .; sudo git commit -m "commit message"

# 5. Create 'psot-update' hook
  $  cd /opt/ecommerce.git/hooks
  $ sudo vi post-update

#Paste the below script:

#!/bin/bash

BRANCH=$(git symbolic-ref --short HEAD 2>/dev/null)

if [ "$BRANCH" = "master" ]; then
    TAG="release-$(date +%F)"
    git tag "$TAG"
fi

# 6. Give executable permission
  $  sudo chmod +x post-update

# 7. Go back to working repo
  $  cd /usr/src/kodekloudrepos/ecommerce

# 8. Now push changes to master
  $  sudo git push origin master

# 9. To verify the tag
  $  sudo git fetch --tag
