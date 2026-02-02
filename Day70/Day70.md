# Day 70: Configure Jenkins User Access

# 1. Login into Jenkins with the given credentials
# 2. Create user
Dashboard > Manage Jenkins > Users > Create user > set user ( Kareem ) with the given details

# 3. Install required plugin
Plugin name: Matrix authorization Strategy

#Install plugin, restart jenkins and re-login

# 4. Give the permissions as mentioned in task
Dashboard > Manage Jenkins > Security > Authorization > Select 'Select Project-based Matrix authorization Strategy'

#First add both users ( admin and the user we have created - Kareem ), then Apply & Save

# 5. Give the read permision to user for the old jobs
Dashboard > Jobs > Configuration > Enable Project-Based security > add user - Kareem, then Apply & Save

# Restart Jenkins and re-login before submitting the task
