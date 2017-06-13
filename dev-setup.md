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
- add the line below to the `/etc/ssh/sshd_config` file

  `PermitRootLogin no`
8. restart ssh

   `sudo service ssh restart`

## Install python3
1. `$ sudo apt-get update`
2. `$ sudo apt-get -y upgrade`
3.  Check the version of python `python3 -V` 
    you should get `Python 3.5.2`
4. install Python Package manaager Pip3

   `$ sudo apt-get install -y python3-pip`
5. Install other development environment tools

   `$ sudo apt-get install build-essential libssl-dev libffi-dev python-dev`
6. Install Python Virtua Environment

   `$ sudo apt-get install -y python3-venv`

## Install mongodb
1. Add MongoDB Repo

   `sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 0C49F3730359A14518585931BC711F9BA15703C6`
2. Add MongoDB Repo detail for `apt`

   `echo "deb [ arch=amd64,arm64 ] http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list`
3. Update Packages 

   `$ sudo apt-get update`
4. Instll MongoDB `mongodb-org` meta-package

   `$ sudo apt-get install mongodb-org`
5. Start the mongo daemon:

   `$ sudo systemctl start mongod`
6. Boot `mongod` on startup

   `sudo systemctl enable mongod`

### Securing MongDB
1. Adding Administrative User
- `$ mongo`
- > use admin
> db.createUser(
>  {
>    user: "mongoAdmin",
>    pwd: "mongoadminpwd",
>    roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
>  }
>)
