# Day 91: Ansible Lineinfile Module

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
- name: Install httpd and creating file on app servers
  hosts: app
  become: yes

  tasks:

    - name: Install httpd package
      yum:
        name: httpd
        state: present

    - name: Ensure httpd service is enabled and running
      service:
        name: httpd
        state: started
        enabled: yes

    - name: Create index file with initial content
      copy:
        dest: /var/www/html/index.html
        content: "This is a Nautilus sample file, created using Ansible!\n"
        owner: apache
        group: apache
        mode: '0777'

    - name: Add new line at the top of index file
      lineinfile:
        path: /var/www/html/index.html
        line: "Welcome to xFusionCorp Industries!"
        insertbefore: BOF

    - name: Ensure correct ownership and permissions
      file:
        path: /var/www/html/index.html
        owner: apache
        group: apache
        mode: '0777'

# 4. Now run the file

$ ansible-playbook -i inventory playbook.yml

# 5. To verify the task, login into any app server and check status of the service!!
