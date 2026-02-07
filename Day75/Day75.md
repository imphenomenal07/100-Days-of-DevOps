# Day 75: Jenkins Slave Nodes

# 1. Login into the jenkins with the given credentials.

# Make sure Java must be install on all APP servers. If not installed, install the java first on all APP servers

# 2. Update old plugins and install new plugins as mentioned then restart jenkins

SSH, SSH Credenatils, SSH Build Agents

# 3. Configure credentails

Dashboard > Manage Jenkins > Security > Credentails > System > Global Credentails > Add Credentails

#Add the credentials for all the app server users: username, password and ID (Server Name)

# 4. Add SSH remote host to perform task

Dashboard > Manage Jenkins > System Configuration > System > SSH remote hosts > Add

#add remote host for all the APP server users: Hostname , port(22), Credentails (username) & check connection before saving

# 5. Add nodes as mentioned in the task

Dashboard > Manage Jenkins > Nodes > Create an Agent Node

#Name:
#Select Permanent, then Ok

#Remote Directory:
#Labels:

#Launch Method: Launch Agent via SSH

#Host: Server Name(stapp01)
#Credentials: Select

Then Save and Apply!!
# Make sure nodes should be online and working properly.

# 6. Create a Freestyle job on any node to verfiy nodes are working on not

Dashbaord > New Item > Job name > Select Freestyle Project > OK

#Select Node Label
#Add execute shell as build step

#In 'Post Command' section, run the below command to verify working state of node

echo 'password-for-app-user' | sudo -S java --version

#Build the job and output, Java version should be there!!
