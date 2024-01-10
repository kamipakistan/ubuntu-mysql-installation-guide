# MySQL Server Installation and Configuration
This repository contains a comprehensive guide and accompanying notebook for installing and configuring MySQL Server on Ubuntu. The step-by-step instructions cover MySQL installation, service management, secure configuration, and common tasks. Use this resource to quickly set up a MySQL database on your Ubuntu system.

## Contents:
1. [MySQL Server Installation Guide](#1-mysql-server-installation-guide)
2. [MySQL Service Management Commands](#2-mysql-service-management-commands)
3. [MySQL Shell Access Instructions](#3-mysql-shell-access-instructions)
4. [Changing Root User Password and Authentication Method](#4-changing-root-user-password-and-authentication-method)
5. [MySQL Secure Installation Steps](#5-mysql-secure-installation-steps)
6. [Verification of MySQL Access](#6-verification-of-mysql-access)
7. [Create a New MySQL User and Database (Optional)](#7-create-a-new-mysql-user-and-database-optional)
8. [Exit MySQL Shell](#8-exit-mysql-shell)
9. [Install MySQL Workbench](#9-install-mysql-workbench)
10. [Additional Tips](#additional-tips)




## 1. MySQL Server Installation Guide

Step 1: Update Package List
```bash
sudo apt update
```

Step 2: Install MySQL Server
```bash
sudo apt install mysql-server
```
## 2. MySQL Service Management Commands
#### Status / Start / Stop / Restart MySQL Service
After the installation, `MySQL server` should start automatically. If not, you can start, stop, or restart it using the following commands:

To check the status of the MySQL service, use the following command:
```bash
sudo systemctl status mysql
```

```bash
sudo systemctl start mysql    # Start MySQL service
sudo systemctl stop mysql     # Stop MySQL service
sudo systemctl restart mysql  # Restart MySQL service
```

## 3. MySQL Shell Access Instructions
Access MySQL Shell
```bash
sudo mysql
```
## 4. Changing Root User Password and Authentication Method
Once you are in the MySQL shell, you can use SQL commands to modify the root user or other settings as needed. For example, to change the root password, you can use the following SQL command:

```sql
# Alter Root User Authentication Method and Set Password
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'new_password';
```
Replace `'new_password'` with your desired password and `exit`.

## 5. MySQL Secure Installation Steps
MySQL comes with a script that can help you secure the installation. Run the following command and follow the on-screen instructions:
```bash
sudo mysql_secure_installation
```
The script provided by MySQL, `mysql_secure_installation`, is a convenient and recommended tool for securing your MySQL installation. It helps you implement several security best practices right after the installation, reducing the risk of potential vulnerabilities. Let's break down the actions it takes:

1. **Setting Root Password:** Assigning a strong password to the root user is crucial for preventing unauthorized access.

2. **Removing Anonymous Users:** Eliminates any MySQL accounts that allow access without a username. This helps in tightening security.

3. **Disallowing Root Login Remotely:** Restricts the root user's ability to log in from remote machines, reducing the attack surface.

4. **Removing the Test Database:** The test database is often an unnecessary security risk. Removing it ensures that potential vulnerabilities associated with it are mitigated.

5. **Reloading Privilege Tables:** This action ensures that the changes made during the script execution take effect immediately.

Running `mysql_secure_installation` is a good practice to follow immediately after installing MySQL to enhance the security of your database server. It provides a guided and systematic approach to securing your MySQL installation.


## 6. Verification of MySQL Access
You can access the MySQL shell with the following command. Enter the root password when prompted.
```bash
sudo mysql -u root -p
```

## 7. Create a New MySQL User and Database (Optional)
For better security, it's recommended to create a dedicated MySQL user and database for your applications. Replace `username`, `password`, and `database_name` with your preferred values:
```bash
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
CREATE DATABASE database_name;
GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'localhost';
FLUSH PRIVILEGES;
```

## 8. Exit MySQL Shell
Exit the MySQL shell by typing:
```bash
exit;
```

## 9: Install MySQL Workbench
MySQL Workbench is a graphical tool for managing MySQL databases. Install it using the following command:

```bash
sudo apt install mysql-workbench
```

## Additional Tips:
* **Firewall Configuration:** If you are using a firewall, make sure to allow traffic on the MySQL port (default is 3306).

* **Configuration File:** MySQL's main configuration file is usually located at `/etc/mysql/mysql.conf.d/mysqld.cnf`. You can edit this file to make changes to the MySQL configuration.

This guide should help you get started with configuring MySQL on Ubuntu. Adjust the steps based on your specific requirements.
