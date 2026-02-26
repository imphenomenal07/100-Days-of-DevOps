# Day 89: Ansible Manage Services

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

    - name: Installing vsftpd
      ansible.builtin.yum:
        name: vsftpd
        state: present
        update_cache: yes

    - name: Ensure vsftpd is running
      service:
        name: vsftpd
        state: started
        enabled: yes

# 4. Now run the file

$ ansible-playbook -i inventory playbook.yml

# 5. To verify the task, login into any app server and check status of the service!!
