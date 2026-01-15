Day9: MariaDB Troubleshooting

1. Login into the DB Server

$ ssh username@server

2. Check status of MariaDB service

$ sudo systemctl status mariadb

3. Restart mariadb service

$ sudo systemctl restart mariadb

# If starts, it's ok. Otherwise troubleshoot service through logs

4. Go to the location: /var/lib/

$ cd /var/lib/

5. Now check, there must be 2 directories: mysql and mysqld
    # ownership should be mysql

6. If any directory is not available, then create and assign ownership to the directories

$ mkdir < name of directory >
$ sudo chown mysql:mysql < name of directory >

7. Now, restart mariadb service & check status

$ sudo systemctl restart mariadb
$ sudo systemctl status mariadb

If service active and running, congrats you have completed your task!!
