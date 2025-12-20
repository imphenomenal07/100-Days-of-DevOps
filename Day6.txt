Day6: Create a Cron Job

1. Login into the server

$ ssh username@servername

2. Check OS to install 'cronie', a cron job runner application
$ cat /etc/or-release

3. Install crone
$ sudo apt/yum install cronie -y

4. Check crond and start
$ sudo systemctl status crond
$ sudo systemctkl start crond

5. Now schedule cron job with below command that will be opened in editor mode
$ sudo crontab -e

Schedule job and save & exit from editor

6. Now check cronjob output
$ cat /tmp/jobname

NOTE: Perform same steps for all users
