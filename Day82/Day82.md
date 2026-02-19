# Day 82: Create Ansible Inventory for App Server Testing

# 1. Go to the location :/home/thor/playbook/
$ cd /home/thor/playbook/

# 2. Check playbook
$ ls

# 3. Create a inventory file
$ vi inventory

#File content:

[app]
stapp01

[app:vars]
ansible_user=tony
ansible_ssh_pass=Ir0nM@n

# 4. Check or test the inventory
$ ansible all -i inventory -m ping

# 5. Go back to the directory: playbook and execute yml file
$ ansible-playbook -i inventory playbook.yml
