Day 2: Temporary user setup with Expiry

1. Login into server with username and password:

$ ssh username@servername

2. Change to roor user:

$ sudo su -

3. Add user to server:

$ useradd username

4. Set Expiry date:

$ chage -E date username


Other commands to add user with expiray date

$ sudo usermod -e date username
$ sudo useradd -e date username
