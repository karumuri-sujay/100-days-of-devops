### Task:

Install and configure SELinux (Security-Enhanced Linux) on App Server 2 as part of a security hardening initiative. While SELinux will be temporarily disabled for initial configuration, this task prepares the system for future mandatory access control implementation.


#### Solution:

Security-Enhanced Linux (SELinux) is a Linux kernel security module providing Mandatory Access Control (MAC), which restricts processes and users to minimum necessary privileges (principle of least privilege).

1. Installation command

   ```
   sudo dnf install selinux-policy selinux-policy-targeted policycoreutils policycoreutils-python-utils -y
   ```
2. Verify whether the SELinux is installed or not using RPM command
3. Open editor from terminal for the location `/etc/selinux/config` with sudo permissions
4. Update the SELINUX to `disabled` from `enforcing`
5. Save the changes and check the status with command `sestatus` -> Output should be disabled
