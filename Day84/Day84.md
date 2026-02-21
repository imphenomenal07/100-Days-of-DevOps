# Day 84: Copy Data to App Servers using Ansible

# 1. Create a inventory file at location
$ vi inventory

#File Content:

[app]

stapp01 ansible_user=tony ansible_ssh_pass=Ir0nM@n

stapp02 ansible_user=steve ansible_ssh_pass=Am3ric@

stapp03 ansible_user=banner ansible_ssh_pass=BigGr33n

# 2. Verify or test inventory file
$ ansible all -i inventory -m ping

# 3. Create yaml playbook to complete the task
$ vi playbook.yml

#File Content

---
- name: Copy index file to app servers
  hosts: app
  become: yes

  tasks:

    - name: Ensure /opt/finance directory exists
      file:
        path: /opt/finance
        state: directory
        mode: '0755'

    - name: Copy index.html from jump host to all app servers
      copy:
        src: /usr/src/finance/index.html
        dest: /opt/finance/index.html
        mode: '0644'

# 4. Run the playbook
$ ansible-playbook -i inventory playbook.yml

# 5. To verify the task, login into any app server and check index file must the present at location!!
