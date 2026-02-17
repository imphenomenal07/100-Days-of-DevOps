# Day 80: Jenkins Chained Builds

# 1. Login into the jenkins with the given credentials.

# 2. Update old plugins and restart Jenkins

# 3. Create a free-style job to fetch latest updates from git

Dashboard > new item > job-name > Select 'Freestyle Project' > Ok

#Add Build step

Build steps > Execute shell > command

sshpass -p "Bl@kW" ssh -o StrictHostKeyChecking=no natasha@ststor01 "cd /var/www/html && git pull origin master"

Then Apply and Save

# 4. Create another free-style job to restart httpd service on all app servers

Dashboard > new item > job-name > Select 'Freestyle Project' > Ok

#Add Build step

Build steps > Execute shell > command

sshpass -p "Ir0nM@n" ssh -o StrictHostKeyChecking=no tony@stapp01 "echo 'Ir0nM@n' | sudo -S systemctl restart httpd"

sshpass -p "Am3ric@" ssh -o StrictHostKeyChecking=no steve@stapp02 "echo 'Am3ric@' | sudo -S systemctl restart httpd"

sshpass -p "BigGr33n" ssh -o StrictHostKeyChecking=no banner@stapp03 "echo 'BigGr33n' | sudo -S systemctl restart httpd"

Then Apply and Save

# 5. Go back first and configure it post build

Dashboard > Click on Job> Configure > Post-build Actions > project to build > project-name > trigger only if build is stable > Apply and Save

# 6. Now build the first and wait until it is finished, now click on second job, it will be built automatically if first job built successfully.
