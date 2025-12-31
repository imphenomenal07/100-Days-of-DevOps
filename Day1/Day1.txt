#Linux user setup with Non-Interactive shell

# path : etc/passwd
# Shell: usr/bin/nologin

# steps to perform the task
#
# 1. Login into the mentioned server with username and password
# 2. Switch to super user with the command: $ sudo su -
#
# 3. Create user: $ sudo useradd username -- shell /sbin/nologin
#
# 4 Now verify the usee: $ cat /etc/passwd
