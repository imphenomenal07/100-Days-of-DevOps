# Day 85: Create Files on App Servers using Ansible

# 1. Create the inventory file to setup creds
$ vi inventory

#File Content:

[app]

stapp01 ansible_user=tony ansible_ssh_pass=Ir0nM@n

stapp02 ansible_user=steve ansible_ssh_pass=Am3ric@

stapp03 ansible_user=banner ansible_ssh_pass=BigGr33n

# 2. Test inventory file connectivity
$ ansible all -i inventory -m ping

# 3. Create a yaml playbook to perform task
$ vi playbook.yml

#File Content:

---
- name: Creating files on app servers
  hosts: app
  become: yes

  tasks:

    - name: Creating files from jump host to all app servers
      file:
        path: /usr/src/nfsshare.txt
        state: touch
        mode: '0777'
        owner: "{{ ansible_user }}"
        group: "{{ ansible_user }}"

# 4. Run the playbook
$ ansible-playbook -i inventory playbook.yml

# 5. To verify the task, login into any app user and check file is create at given location. Also check file ownership!!
