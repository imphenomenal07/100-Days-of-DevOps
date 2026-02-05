# Day 73: Jenkins Scheduled Jobs

Click on the Jenkins button on the top bar to access the Jenkins UI. Login using username admin and password Adm!n321

1. Create a Jenkins jobs named copy-logs.

2. Configure it to periodically build every 11 minutes to copy the Apache logs (both access_log and error_logs) from App Server 2 (from default logs location) to location /usr/src/sysops on Storage Server.


# 1. Login into Jenkins with the given credentials.

# 2. Update old plugins and add new plugins as mentioned below
SSH, SSH Credentails, SSH Build Agents, SSH Pipeline Steps, Publish over SSH

#Then restart jenkins and re-login

# 3. Configure credentails
Dashboard > Manage Jenkins > Security > Credentails > System > Global Credentails > Add Credentails

#Add the credentials for both users: username, password and ID (anything)

# 4. Add SSH remote host to perform task
Dashboard > Manage Jenkins > System Configuration > System > SSH remote hosts > Add

#add remote host for both users: HOstname , port(22), Credentails (username) & check connection before saving

# 5. create job
Dashboard > new items > job-name > freestyle project > ok

#Triggers > Build periodically 

*/11 * * * *

#Add build steps:

Build steps > Execute shell script on remote host using ssh > command

sshpass -p 'Bl@kW' scp -p -o StrictHostKeyChecking=no /var/log/httpd/* natasha@ststor01:/usr/src/sysops

# Then Apply - Save and click on 'Build Now'

#If there is any issues, fix the re-build the job
