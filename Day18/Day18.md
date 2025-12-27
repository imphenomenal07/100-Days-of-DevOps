# Day19: Install and Configure Web Application

# 1. Login into all APP servers
$ ssh user@servver

# 2. Install httpd service and php on APP servers
$ sudo yum install httpd -y
$ sudo yum install php -y 

# 3. Now configure httpd service on the required port number
$ vi /etc/httpd/conf/httpd.conf

Search for the word 'LISTEN' in conf file and update port 80 to mentioned in task

# 4. Enable, restart and check status of httpd service
$ sudo systemctl enable httpd;  sudo systemctl restart httpd;  sudo systemctl status httpd

# 5. Now login into DB server
$ ssh user@server

# 6. Install MariaDB service

sudo dnf update -y
sudo dnf install mariadb-server mariadb -y
sudo systemctl start mariadb
sudo systemctl enable mariadb
sudo systemctl status mariadb

# 7 Login into DB
sudo mysql -u root -p

# 8. Now create the database
CREATE DATABASE db_name;

# 9. Create user and grant all privilages then apply changes

$ CREATE USER 'db_username'@'localhost' IDENTIFIED BY 'password';
$ GRANT ALL PRIVILEGES ON db_name.* TO 'db_username'@'%';
$ FLUSH PRIVILEGES;

# Now try to connect to app
