# Day 90: Managing ACLs Using Ansible

# 1. Inventory is already created, go to location and ping file
$ ansible all -i inventory -m ping

# 2. Create a yaml playbook to perform task
$ vi playbook.yml

#File Content:

---
- name: Creating file on app server1
  hosts: stapp01
  become: yes

  tasks:

    - name: Creating files from jump host to app server1
      ansible.builtin.file:
        path: /opt/devops/blog.txt
        state: touch
        mode: '0777'
        owner: "{{ ansible_user }}"
        group: "{{ ansible_user }}"

    - name: Set ACL read permission for group tony
      ansible.posix.acl:
        path: /opt/devops/blog.txt
        entity: tony
        etype: group
        permissions: r
        state: present

- name: Creating file on app server2
  hosts: stapp02
  become: yes

  tasks:

    - name: Creating files from jump host to app server2
      ansible.builtin.file:
        path: /opt/devops/story.txt
        state: touch
        mode: '0777'
        owner: "{{ ansible_user }}"
        group: "{{ ansible_user }}"

    - name: Set ACL read permission for group tony
      ansible.posix.acl:
        path: /opt/devops/story.txt
        entity: steve
        etype: user
        permissions: rw
        state: present

- name: Creating file on app server3
  hosts: stapp03
  become: yes

  tasks:

    - name: Creating file from jump host to app server3
      ansible.builtin.file:
        path: /opt/devops/media.txt
        state: touch
        mode: '0777'
        owner: "{{ ansible_user }}"
        group: "{{ ansible_user }}"

    - name: Set ACL read permission for group tony
      ansible.posix.acl:
        path: /opt/devops/media.txt
        entity: banner
        etype: group
        permissions: rw
        state: present

# 3. Run the playbook
$ ansible-playbook -i inventory playbook.yml

# 4. To verify the task, login into any app user and check file is create at given location. Also check file permissions!!
