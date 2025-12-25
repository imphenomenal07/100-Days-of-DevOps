# Day16: Install and Configure Nginx as an LBR

1. Login into LB server: $ ssh user@server

2. Check status of Nginx server, if installed: $ sudo systemctl status nginx

3. If not installed, check OS distribution: $ cat /etc/os-release

4. Now install nginx: $ sudo yum install nginx -y

5. Now start and check status of nginx service: $ sudo systemctl start nginx; sudo sytemctl status nginx

6. Login into any app server get httpd service port: $ sudo ss -tunlp | grep httpd

7. Now update config file as per the task: $ sudo vi /etc/nginx/nginx.conf

# Add upstream anywhere in config file, syntax should be correct


    upstream appservers {

        server stapp01:httpd-service-port;
        server stapp02:httpd-service-port;
        server stapp03:httpd-service-port;
    
    }

# Add location below the listen server

location / {
            proxy_pass http://appservers;
}

Now save and exit from conf file.
The restart service and check status.

8. If there is any issues in conf file, run the below command to find issues:
$ sudo nginx -t

If there is no issues, service up and runnig fine that means you have compeled the task!!
