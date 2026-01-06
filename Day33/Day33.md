# Day33: Resolve Git Merge Conflicts

# 1. Login into the max server with storage host
  $  ssh max@ststor01
  #password: Max_pass123

# 2. Go to the repo
  $  cd stroy-blog/

# 3. Check git status, fetch latest updates and check list of files
  $  git status; git fetch; ls

# 4. Print content of 'story-index.txt' file.
  $ vi story-index.txt
  #Here you will see typo 'mooose'. Update it to 'mouse'.
  #Also you will see here 4 story titles.

# 5. Login into 'Gitea UI' with any of the user
  #Now check the 'story-index.txt' file. If there is no 4th story title, add the title and save the file.

# 6. Now add all files
  $  git add .

# 7. Make a commit
  $ git commit -m "commit message"

# 8. Push files to master with the user 'max'
  $  git push origin master
  #If there is any push conflict, forcefully push the files.
