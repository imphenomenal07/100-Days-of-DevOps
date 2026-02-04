# Day 72: Jenkins Parameterized Builds

# 1. Login into Jenkins with the given credentials

# 2. Create a free filestyle job

Dashboard > new item > name-of-job > select 'freestyle' > click 'OK'

# 3. Enable parameters and Add parameter for the job

Click Add Parameter → String Parameter

Configure it as:

Name: Stage

Default Value: Build

# 4. Add choice parameter

Click Add Parameter → Choice Parameter

Configure it as:

Name: env

Choices:

Development
Staging
Production

# 5. Configure shell command to execute

Configure the shell command

Scroll to Build

Click Add build step → Execute shell

Add the following command:

echo $Build
echo $env

# Apply and Save the job, then run job 'Build with Parameter'
