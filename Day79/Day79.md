# Day 79: Jenkins Deployment Job

# 1. Login into the jenkins with the given credentials.

# 2. Update old plugins and install new plugins as mentioned then restart jenkins

SSH, SSH Credenatils, SSH Build Agents, Publish over SSH, Git, Git Client, Gitea

# 3. Install 'httpd' service on all APP SERVERS and configure the port

$ sudo yum install -y httpd

$ sudo sed -i 's/Listen 80/Listen 8080/' /etc/httpd/conf/httpd.conf

$ sudo systemctl enable httpd; sudo systemctl start httpd; systemctl status httpd

# 4. Login into storage server with 'Sarah' user to cloned repo permissions

$ ssh sarah@stor01
pass: Sarah_pass123

#Check the permissions

ls -l /var/www/html

#user and group, both will be sarah

# 5. Login with Jenkins, create ssh keys and copy them to storage server under sarah user

$ ssh-keygen -t rsa

#Copy the content of public and paste to storage server under sarah user

#If '~/.ssh' directory not available on server, create one then paste content inside the file 'authorized_keys'
$ vi authorized_keys

# 6. Add credentials in Jenkins for the user 'sarah'

Dashboard > Manage Jenkins > Security > Credentails > System > Global Credentails > Add Credentails

#Add the credentials for storage server user: username(sarah), password(Sarah_pass123) and ID(ststor01)

# 7. Create a Jenkins job

Dashboard > create a job > new item > job-name > free style project > OK

#Source Code Management

Repository URL:
Credentials: sarah

#Trigeers > Poll SCM > Schedule: * * * * *

#Apply & Save

# 8. Login again into storage server with 'sarah' user and update index file content as mentioned in the task

$ cd /var/www/html

$ vi index.html

#Update content & push to git

$ git add .
$ git commit -m "commit message"
$ git push

# 9. Go back to Jenkins and check new job built or not. If yes, click on the 'APP Button', updated content must be visible in browser!!
