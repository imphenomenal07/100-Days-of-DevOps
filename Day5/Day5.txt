Day5: SELinux installation and configuration

1. Check os
$ cat /etc/or-release

2. Check if the SELinux is already installed or not
$ sestatus

if you get "SELINUX = disable", means SELinux is installed. In case of error, not installed.

3. Install SELinux, if not installed

$ sudo dnf install -y \
  selinux-policy \
  selinux-policy-targeted \
  policycoreutils \
  policycoreutils-python-utils \
  setools-console

4. Disable SELinux if enable or enforcing
$ sudo vi /etc/selinux/config

set "SELINUX=enforcing" to "SELINUX=disable" as per tasks requirement
