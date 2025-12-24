# Day14:  Linux Process Troubleshooting

1. As per the given task, login into all APP servers
$ ssh user@server

2. Now check status of 'httpd' service on all servers
$ sudo systemctl status httpd

3. Now check which process is using http servuce port
$ sudo netstat -luntp | grep 8085
OR
$ sudo ss -luntp | grep 8085

4. Now kill the process that is http service port
$ sudo kill <PID>

5. Now restart the service and check status
$ sudo systemctl restart httpd; sudo systemctl status httpd

6. Final to call the service, go to jump host in new terminal and perfrom the below commands

$ curl http://staap01:8085
$ curl http://staap02:8085
$ curl http://staap03:8085

If you are not getting expected out, check service logs and restart the service again!!
