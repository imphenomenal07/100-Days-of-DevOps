Day: Install Ansible

1. Check the OS
$ cat /etc/os-release

2. Check dependenices

$ pyhton3 --version
$ pip3 --version

3. Install Ansible with the mentioned version
$ sudo apt/yum install ansible==<version>

4.Then recheck

$ which ansible
$ ansible --version
