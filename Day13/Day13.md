# Day13: IPtables Installation And Configuration

1. Login into all APP servers
$ ssh user@server

2. Check OS distribution to install service
$ cat /etc/os-release

3. Now install iptbales service on all APP servers
$ sudo apt/yum install iptables-services -y

4. Now start service and check status
$ sudo systemctl start iptbales; sudo systemctl status iptables

5. Check firewall rules
$ sudo iptables -L -n

6. Check if any service running the port number
$ sudo ss -lntp | grep portnumber

7. Now add the traffic rule for the port number
$ sudo iptables -I INPUT 1 -p tcp --dport portnumber -j ACCEPT

8. Block traffic for others
$ sudo iptables -A INPUT -p tcp --dport portnumber -j DROP

9. Now save the rule
$ service iptable save

10. Now restart service and check status
$ sudo systemctl restart iptables; sudo systemctl status iptables

11. Not login into LB server and do telnet
$ ssh user@server
$ telnet server portnumber < telnet stlb01 portnumber>

If there is any error, check httpd and iptables service logs
