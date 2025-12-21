# Day10: Linux Bash Script

1. Login into the server

$ ssh username@server

2. Install zip to run task on server

$ sudo yum install zip -y

3. Create script as per the requirement

$ vi /scripts/official_backup.sh

#!/bin/bash

zip -r backup/xfusioncorp_blog.zip /var/www/html/official

scp backup/xfusioncorp_blog.zip clint@stbkp01:/backup

Now save and exit from the script

4. Give executable permission to script

$ chmod +x /scripts/official_backup.sh

# For passwordless execution on Backup server, create ssh key and copy it to backup user

5. Create access key

$ ssh-keygen -t rsa

6. Copy it to backup server

$ ssh-copy-id clint@stbkp01

# Now run the script

7. $ bash /scripts/official_backup.sh

