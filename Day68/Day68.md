# Day 68: Set Up Jenkins Server

# 1. Login into jenkins server with root user from Jump-host, password mentioned in task
$ ssh root@jenkins

# 2. Install Jeknins with yum packages

#First install java17 or java21
$ sudo yum install -y java-17-openjdk

#Import GPG key
$ sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key

#Add working repo
$ sudo tee /etc/yum.repos.d/jenkins.repo <<EOF
[jenkins]
name=Jenkins-stable
baseurl=https://pkg.jenkins.io/redhat-stable
gpgcheck=1
EOF

#Install jenkins
$ sudo yum install -y jenkins

#If there is any GPG failue issue, use below command to install jenkins
$ sudo yum install -y jenkins --nogpgcheck

#Enable - start jenkins and check status
$ sudo systemctl start jenkins; sudo systemctl enable jenkins; sudo systemctl status jenkins

# 3. Click on APP button and login with initial password
$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword

# 4. Go with suggested plugins and setup username-password as mentioned in the task
