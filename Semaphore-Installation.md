## Semaphore
[Semaphore](https://github.com/semaphoreui/semaphore) is a modern web interface for managing popular DevOps tools. Semaphore UI allows you to: Easily run Ansible playbooks, Terraform and OpenTofu code, as well as Bash and PowerShell scripts. Receive notifications about failed tasks. Control access to your deployment system.
<br>

## Installation

## Installing MariaDB

First, we need to install a database server. For this, we will be using [MariaDB](https://mariadb.org/). to install the server and client packages, we will use the command:
```
apt install mariadb-server mariadb-client
```
<br>

We will then need to secure the database using the command:
```
mariadb-secure-installation
```
<br>

Set the following once prompted:
```
Switch to unix_socket authentication [Y/n] n

Change the root password? [Y/n] y

Remove anonymous users? [Y/n] y

Disallow root login remotely? [Y/n] y

Remove test database and access to it? [Y/n] y

Reload privilege tables now? [Y/n] y
```
<br>

To check if it's now running, we can use the command ```systemctl status mariadb```.
![image](https://github.com/user-attachments/assets/5d1a40e2-b195-4de0-b87c-c280d6e1eaa5)
<br>

## Installing Semaphore

In this demo, We will be installing Semaphore on a Ubuntu machine using the ```wget``` command:
<br>
```
wget https://github.com/semaphoreui/semaphore/releases/\
download/v2.15.0/semaphore_2.15.0_linux_amd64.deb

sudo dpkg -i semaphore_2.15.0_linux_amd64.deb
```
![image](https://github.com/user-attachments/assets/6ac7ce55-9938-4f74-a565-3708f691e990)
<br>

To check if it's installed, we can use the command ```semaphore version```.
![image](https://github.com/user-attachments/assets/7c5da229-db22-46a9-9304-b4b2fa98e8c8)
<br>

Next, We will need to setup semaphore using the command:
```
semaphore setup
```
<br>

Kindly copy the following answers:
```
Hello! You will now be guided through a setup to:



1. Set up configuration for a MySQL/MariaDB database

2. Set up a path for your playbooks (auto-created)

3. Run database Migrations

4. Set up initial semaphore user & password



What database to use:

   1 - MySQL

   2 - BoltDB

   3 - PostgreSQL

 (default 1): 1

   DB Hostname (default 127.0.0.1:3306): 127.0.0.1:3306

   DB User (default root): root

   DB Password:   

   DB Name (default semaphore): semaphore

   Playbook path (default /tmp/semaphore): /opt/semaphore

   Web root URL (optional, example http://localhost:8010/):  http://localhost:8010/

   Enable email alerts (y/n, default n): n

   Enable telegram alerts (y/n, default n): n

   Enable LDAP authentication (y/n, default n): n
```
<br>

Once finished, it will then ask for the following and on this section, we will be using an example:
```
Username: admin

Email: admin@example.com

WARN[0268] sql: no rows in result set                    level=Warn

 Your name: user

 Password: **********

 You are all setup Admin User!

 Re-launch this program pointing to the configuration file

 ./semaphore server --config /home/ubuntu/config.json



To run as daemon:

 nohup ./semaphore server --config /home/ubuntu/config.json &

 You can login with admin@example.com or admin.
```
<br>

We can now run semaphore using this command:
```
semaphore server --config=./config.json
```
<br>

We can now access it via ```https://localhost:3000/```

![image](https://github.com/user-attachments/assets/c4445486-9f51-4f1d-a2a2-b97ac03b5f39)
<br>

![image](https://github.com/user-attachments/assets/07a37b8e-ad54-4ade-9cdd-35f52c2d8866)










