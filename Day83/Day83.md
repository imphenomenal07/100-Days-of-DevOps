# Day 83: Troubleshoot and Create Ansible Playbook

# 1. Go to the location :/home/thor/ansible/
$ cd /home/thor/ansible/

# 2. There is already inventory file, update the file accordingly
$ vi inventory

#File content:

[app]
stapp01

[app:vars]
ansible_user=tony
ansible_ssh_pass=Ir0nM@n

# 3. Check or test the inventory
$ ansible all -i inventory -m ping

# 4. Create a ansible playbook to do the task
$ vi playbook.yml

#File Content:

---
- name: Create file on App Server 1
  hosts: stapp01
  become: yes
  tasks:
    - name: Create empty file /tmp/file.txt
      file:
        path: /tmp/file.txt
        state: touch

#Save and exit from file.

# 5. Now execute the playbook
$ ansible-playbook -i inventory playbook.yml

# To verify the task, login into APP server 1 and check the /tmp directory. File will be available there!!
