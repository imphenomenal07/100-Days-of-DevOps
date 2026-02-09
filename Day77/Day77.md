# Day 77: Jenkins Deploy Pipeline

# 1. Login into the jenkins with the given credentials.

# 2. Update old plugins and install new plugins as mentioned then restart jenkins

SSH, SSH Credenatils, SSH Build Agents, Pipeline, Pipeline Stage View, Git, Git Client

# 3. Configure credentails

Dashboard > Manage Jenkins > Security > Credentails > System > Global Credentails > Add Credentails

#Add the credentials for storage server user: username, password and ID 

# 4. Add SSH remote host to perform task

Dashboard > Manage Jenkins > System Configuration > System > SSH remote hosts > Add

#add remote host for storage server users Hostname , port(22), Credentails (username) & check connection before saving

# 5. Add nodes as mentioned in the task

Dashboard > Manage Jenkins > Nodes > Create an Agent Node

#Name: Storage Server
#Select Permanent, then Ok

#Remote Directory: /var/www/html
#Labels: ststor01

#Launch Method: Launch Agent via SSH

#Host: Server Name(ststor01)
#Credentials: select 'natasha'

Then Save and Apply!!
# Make sure node should be online and working properly.

# 6. Now go back to terminal and login into storage server
$ ssh natasha@ststor01

#Install java
$ sudo yum install -y java

#Check ownership of /html directory
$ cd /var/www; ls -l

#Ownership will be assigned to git user 'sarah' then change it to user 'natasha'
$ sudo chown -R natasha html 

# 7. Create Jenkins Pipeline job

Dashboard > New Item > Job Name > OK

#Scripts

pipeline {
    agent {
        label 'ststor01'
    }

    stages {
        stage('Deploy') {
            steps {
                sh "git clone http://git.stratos.xfusioncorp.com/sarah/web_app.git /tmp/app"
                sh "echo 'Bl@kW' | sudo -S cp -r /tmp/app/* /var/www/html/"
            }
        }
    }
}

# Apply and Save, then build the Job

# If there is any build fails, check console output and troubleshoot issue, fix it and re-build the job!!
