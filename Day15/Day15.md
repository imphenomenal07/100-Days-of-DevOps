# Day15: Setup SSL for Nginx

1. Login into the server: $ ssh user@server
2. Check the if certs and private key available at /tmp location: $ ls /tmp
3. Check OS distribution to install nginx: $ cat /etc/os-release
4. Install nginx: $ sudo yum install nginx -y
5. Now start service and check status: $ sudo systemctl start nginx; sudo systemctl status nginx
6. Now move cert and key to correct location

$ mv /tmp/nautilus.certs /etc/pki/tls/certs/nautilus.certs
$ mv /tmp/nautilus.key /etc/pki/tls/private/nautilus.key

7. Now update server details in config file: $ vi /etc/nginx/nginx.config

Now add server IP and update certs and private key path in TLS. Also uncomment whole TLS block

8. As per the task, update Index.html file: $ cd /usr/share/nginx/html
 First remove old Index.hmtl file: $ sudo re -rf Index.html
 Create new one and update content: $ sudo vi Index.html
 Save and quit

9. Now restart service and check status: $ sudo systemctl restart nginx; sudo systemctl status nginx
10. To nginx config details: $ sudo nginx -t
11. Now go to jusp host server and call the service: $ curl -Ik https://server-IP/


# Summi the task if there is no error!!
