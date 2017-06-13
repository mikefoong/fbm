# Setup Documentation
Setup from scratch on Digital Ocean with Ubuntu 16.04.02.

## Initial Setup
1. Create a droplet on Digital Ocean
2. Logon using PuTTY
3. Default root password is in the email
4. Required to change password upon first login
- login as root with the default password
- prompt sequence:
 - Initial Password
 - New Password
 - Repeat New Password
5. Create a new user

   `# adduser newuser`
- add a password
- add other information
6. Add sudo capabilities for `newuser`

   `# usermod -aG sudo newuser`
7. Disable remote ssh login for root
- add the line below to the `/etc/ssh/ssh_config` file

  `PermitRootLogin no`
8.
   
