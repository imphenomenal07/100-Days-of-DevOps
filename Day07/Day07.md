Day7: Linux SSH Authentication

1. For Passwordless, we need SSH key to login

$ ssh-keygen -t rsa  #TO GENERATE SSH KEY

2. Go to key location
$ cd .ssh

3. COPY KEY to all users

$ ssh-copy-id user@server

#Perfrom same step for all user

4. Try to login into all user, password will not be required now
$ ssh username@server
