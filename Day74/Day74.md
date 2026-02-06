# Day 74: Jenkins Database Backup Job

# 1. Login into the jenkins with the given credentials.

# 2. Update old plugins and install new plugins as mentioned then restart jenkins

SSH, SSH Credenatils, Publish over SSH

# 3. Configure credentails

Dashboard > Manage Jenkins > Security > Credentails > System > Global Credentails > Add Credentails

#Add the credentials for both users: username, password and ID (anything)

# 4. Add SSH remote host to perform task

Dashboard > Manage Jenkins > System Configuration > System > SSH remote hosts > Add

#add remote host for both users: HOstname , port(22), Credentails (username) & check connection before saving

# 5. create job

Dashboard > new items > job-name > freestyle project > ok

#Triggers > Build periodically 

*/10 * * * *

#Add build steps:

Build steps > Execute shell script on remote host using ssh > command


mysqldump -u kodekloud_roy -p'asdfgdsd' kodekloud_db01 > db_$(date +%F).sql

sshpass -p 'H@wk3y3' scp -o StrictHostKeyChecking=no db_$(date +%F).sql clint@stbkp01:/home/clint/db_backups


# Then Apply - Save and click on 'Build Now'

#If there is any issues, fix the re-build the job
