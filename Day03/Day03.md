Secure Root SSH Access

This task needs to be perfomred on all APP SERVERS: stapp01. stapp02 and stapp03

1. Login into server:
$ ssh username@servername

2. Switch to root user
$ sudo su -

3. Check for config files:

$ sudo vi /etc/ssh/sshd_config

File will be opened in vim editor mode.
Now search for "PermitRootLogin"

If it is "yes", update it to "no"

Now save and exit from the editor mode

4. Now restart sshd service
$ sudo systemctl restart sshd


#Perfrom same steps for all users
