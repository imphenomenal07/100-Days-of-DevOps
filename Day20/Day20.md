# Day20: Configure Nginx + PHP-FPM Using Unix Sock

# 1. Login into the server
 $ ssh user@server

# 2. Install nginx and configure the port in 'nginx.conf' file
 $ sudo yum install nginx -y
 $ vi /etc/nginx/nginx.conf #open conf file in editor mode

 Now to go the LISTEN Section update port number 80 to other

 Change root path as mentioned in the task
 root /var/www/html;

 Also add index files below listen
 index index.php index.html;
 
 Save and quit from the file.

# 3. Install php-fpm version as mentioned in the task
 dnf install -y epel-release
dnf install -y https://rpms.remirepo.net/enterprise/remi-release-9.rpm

dnf module reset php -y
dnf module enable php:remi-8.3 -y

dnf install -y php php-fpm php-cli php-common php-mysqlnd php-curl php-xml php-mbstring

php -v

mkdir -p /var/run/php-fpm
chown nginx:nginx /var/run/php-fpm
chmod 755 /var/run/php-fpm

# 4. Now configure unix socket
 $ vi /etc/php-fpm.d/www.conf

 Update the below details

 user = nginx
group = nginx

listen = /var/run/php-fpm/default.sock

listen.owner = nginx
listen.group = nginx
listen.mode = 0660


# 5. Start and enable php-fpm

 systemctl enable --now php-fpm
systemctl restart php-fpm


# 6. Configure nginx and php-fpm to work together
 Open nginx.conf file and update the location details inside server block

 location ~ \.php$ {
        include fastcgi_params;
        fastcgi_pass unix:/var/run/php-fpm/default.sock;
        fastcgi_index index.php;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }

# 7. Start and enable both services

 sudo systemctl enable --now php-fpm
sudo systemctl enable --now nginx

# 8. To validate 
 $ curl http://stapp01:portnumber/index.php


# 9. For final submission, do curl from Jump Host server
  $ curl http://stapp01:portnumber/index.php
