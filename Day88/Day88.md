# Day 88: Ansible Blockinfile Module

# 1. Go to the location and there is inventory file, update it

$ vi inventory

#add app as host

[app]

# 2. Test the inventory file connectivity

$ ansible all -i inventory -m ping

# 3. Create a yaml playbook to complete mentioned tasks

$ vi playbook.yml

#File content:

---
- name: Installing packages on app servers
  hosts: app
  become: yes

  tasks:

    - name: Installing httpd
      ansible.builtin.yum:
        name: httpd
        state: present
        update_cache: yes

    - name: Ensure httpd is running
      service:
        name: httpd
        state: started
        enabled: yes

    - name: Add content to /var/www/html/index.html
      blockinfile:
        path: /var/www/html/index.html
        create: yes
        owner: apache
        group: apache
        mode: '0755'
        block: |
          Welcome to XfusionCorp!

          This is Nautilus sample file, created using Ansible!

          Please do not modify this file manually!

# 4. Now run the file

$ ansible-playbook -i inventory playbook.yml

# 5. To verify the task, login into any app server and check status of the service!!
