# Day27: Git Revert Some Changes

# 1. Login into storage server
  $ ssh user@host

# 2. Go to the repo
  $ cd /usr/src/kodekloudrepos/official

# 3. Check git status and logs
  $ sudo git status
  $ sudo git log

# 4. Revert the latest commit(HEAD) without editing
  $ sudo git revert HEAD --no-edit

# 5. Now amend the commit
  $ sudo git commit --amned -m "revert official"

# 6. Push to HEAD, if required
  $ sudo git push origin HEAD
