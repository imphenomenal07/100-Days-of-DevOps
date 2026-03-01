# Day 92: Managing Jinja2 Templates Using Ansible

# 1. Go to the location and check the inventory file YAML playbook

If host name missing in playbook, update and save the file!!

# 2. Ping the inventory file to verify connections

$ ansible all -i inventory -m ping

# 3. Create a jinja2 templates

Go to location: ansible/role/httpd/templates

#Create file:

$ vi index.html.j2

#Add content: This file was created using Ansible on {{ inventory_hostname }}

# 4. Add task in role

Go to location: ansible/role/httpd/tasks

#Add task in main.yml file

$ vi main.yml

- name: Copy index.html template
  template:
    src: index.html.j2
    dest: /var/www/html/index.html
    owner: tony
    group: tony
    mode: '0777'

# 5. Now run the playbook inside 'ansible' directory

$ ansible-playbook -i inventory playbook.yml

# If there is any issues, troubleshoot and fix it !!
