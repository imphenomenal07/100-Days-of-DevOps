# Day 93: Using Ansible Conditionals

# 1. Go the 'ansible' location and ping the inventory file to check connectivity

$ ansible all -i inventory -m ping

# 2. Create a YAML playbook to complete task

$ vi playbook.yml

#File Content:

- name: Using Ansible Conditions
  hosts: all
  become: true
  tasks:
    - name: Show hostname for debugging
      ansible.builtin.debug:
        msg: "Hostname is: {{ ansible_hostname }}"

    - name: Copy for server 1
      ansible.builtin.copy:
        src: /usr/src/dba/blog.txt
        dest: /opt/dba
        owner: "{{ ansible_user }}"
        group: "{{ ansible_user }}"
        mode: '0655'
      when: ansible_hostname == "stapp01"

    - name: Copy for server 2
      ansible.builtin.copy:
        src: /usr/src/dba/story.txt
        dest: /opt/dba
        owner: "{{ ansible_user }}"
        group: "{{ ansible_user }}"
        mode: '0655'
      when: ansible_hostname == "stapp02"

    - name: Copy for server 3
      ansible.builtin.copy:
        src: /usr/src/dba/media.txt
        dest: /opt/dba
        owner: "{{ ansible_user }}"
        group: "{{ ansible_user }}"
        mode: '0655'
      when: ansible_hostname == "stapp03"

# 3. Run the file to complete the task

$ ansible-playbook -i inventory playbook.yml

# If there are any issues, find it and fix it!!
