# Day 86: Ansible Ping Module Usage

# 1. Go to the directory ansible and check there is inventory file
$ cd ansible
$ ls

# 2. Check the content of inventory file, make sure file should be in below format for all APP users

stapp01 ansible_user=tony ansible_host=host-ip ansible_ssh_pass=password

# 3. Ping the module on required APP server, for example for stapp01
$ ansible stapp01 -i inventory -m ping

# If there is any errors, re-check inventory file and fix it!!
