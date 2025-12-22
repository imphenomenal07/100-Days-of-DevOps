# Day11: Install and Configure Tomcat Server

Move war file jumphost to app server
$ scp /tmp/ROOT.war tony@stapp01:/tmp

1. Login into serer
$ ssh username@server

2. Check OS distribution
$ cat /etc/os-release

3. Install tomcat
$ sudo yum install tomcat -y

# Configure tomcat to run on port 8084

5. Go to the below directory
$ cd /etc/tomcat

6. Search for "server.xml" and open in editor mode
$ vi server.xml

<Search for connector port

Connector port="8080" protocol="org.apache.coyote.http11.Http11NioProtocol"

Now change connector port "8080" to "8084", save and quit>

7. Now move war file to correct location

$ sudo mv /tmp/ROOT.war /usr/share/tomcat/webapps/

8. Update ownership

$ sudo chown tomcat:tomcat /usr/share/tomcat/webapps/ROOT.war

9. Now enable and start the service

$ sudo systemctl enable tomcat
$ sudo systemctl start tomcat

10. Now call the service on the app server

$ curl http://stapp01:8084
