# Day12: Linux Network Services

1. Telnet into all server and which server has connectivity issue
$ telent servername < Port number >

$ telnet stapp01 6000

2. Login into the server which has connectivity issue
$ ssh user@server

3. Check status of httpd service
$ sudo systemctl status https

4. If service is failed, try to restart
$ sudo systemctl restart httpd

Perform telnet task in new terminal on jump host server, if service is started.

5. If you still face connectivity issue, then perfrom netstat task
$ sudo netstat -lntp | grep < port number >

this is to check which process is using port number

6. Now kill/terminate the process
$ sudo kill < Process ID >

7. Now restart the httpd service and check status. If this active and running, do telnet in another terminal.
If still the connectivity issue, perform below tasks

8. Check IP tables execution rules
$ sudo iptable -L -n

9. Now add the new rule with accept policy with our port number
$ sudo iptable -I INPUT 1or5 -p tcp --dport <PortNumber> -i ACCEPT

<-I INPUT 1> or <-I INPUT 5> : To set process execution priority
