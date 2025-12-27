# Day19: Install and Configure Web Application

# 1. Login into the server
$ ssh user@server

# 2. Install Apache service (httpd)
$ sudo yum install httpd -y

# 3. Now configure and port number as mentioned in the task
$ sudo vi /etc/httpd/conf/httpd.conf

Search for the keyword 'LISTEN' and update the port 80 to other

# 4. Copy index.html files to server
 Open just host server in new terminal and copy files from host to server
 Before copying files, create 'beta' and 'apps' directory on server

 $ sudo scp ~/apps/index.html steve@stapp02:/home/steve/apps
 $ sudo scp ~/beta/index.html steve@stapp02:/home/steve/beta

# 5. Now setup the Index files at correct location

 $ sudo mv /apps/index.html /var/www/html/apps
 $ sudo mv /beta/index.html /var/www/html/beta

# 6. Now enable and restart service and check status

$ sudo systemctl enable httpd; sudo systemctl restart httpd; sudo systemctl status httpd

# Check the if everything setup correclty or not

$ curl http://;localhost:portnumner/beta/
$ curl http://;localhost:portnumber/apps/

In case of any issues, check the index files are setup correctly at exact location and service listing on the required port number
