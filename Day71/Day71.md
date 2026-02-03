# Day 71: Configure Jenkins Job for Package Installation

# 1. Login into jenkins with the given credentials

# 2. Update old plugins
# 3. Install new plugin
SSH, SSH Credentails, SSH Build Agents
#Restart and re-login jenkins

# 4. Update storage server details in jenkins
Dashboard > Manage Jenkins > Security > Credentails > System > Global Credentails (unrestricted) > Add credentials

#Username - natasha
#Password - Bl@kW
#ID - storgae server

# 5. Add ssh remote host
Dashboard > Manage Jenkins > System > SSH remote hosts > add

#Hostname - ststor01.stratos.xfusioncorp.com
#Port - 22
#Credentails - natasha

#Click on 'Check connection' and before clicking on 'Apply and Save'

# 6. Create a free-style job
Dashboard > new item
#item name - install-packages
#click on 'freestyle project' and then click on 'OK'

# Click on 'This project is parameterized'
#Click on 'Add parameter' and select 'String Parameter'

#NAME - PACKAGE
#Default Value - any

# Build Step

#Click 'Add build step' and select 'Execute shell script on remote host using ssh'

Command - echo 'Bl@kW' | sudo -S yum install -y $PACKAGE

#SAve the job

# 7. Build the job
Click on 'Build with parameters'

#Give the name of any package in Defalut value: nginx

#Once the job is executed, login into storage server and verify the package is installed or not
