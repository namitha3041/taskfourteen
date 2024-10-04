Task Fourteen - Steps for Setting Up a Web Server on Cloud VM
Description:
This repository contains detailed steps for setting up a web server on a cloud-hosted Virtual Machine (VM). The setup includes SSH login, cloning an HTML page, setting up Apache, installing PHP and MySQL, and creating a registration and login system with PHP.

Steps:
1. Login to Your Cloud VM via SSH from Kali Linux
Open your Kali Linux terminal.
Use the following SSH command to log in to your VM:
bash
Copy code
ssh -i /path-to-private_key username@<your-vm-public-ip>
Screenshot: Capture a screenshot showing successful SSH login.
2. Clone the Repository from Tasktwelve
After logging into the VM, clone your task12 repository from GitHub:
bash
Copy code
git clone https://github.com/yourusername/tasktwelve.git
3. Copy the Cloned Files to Apache Web Server Root Directory
Copy the HTML and related files from the cloned task12 folder to the root directory of the Apache webserver:
bash
Copy code
sudo cp -r tasktwelve/* /var/www/html/
4. Start the Apache Web Server
Ensure Apache is installed (if not, install it using):
bash
Copy code
sudo apt install apache2
Start the Apache web server:
bash
Copy code
sudo systemctl start apache2
Verify the Apache service is running:
bash
Copy code
sudo systemctl status apache2
5. Access the Web Page via Local Browser
Open a web browser on your local machine and enter the public IP of your cloud VM:
bash
Copy code
http://<your-vm-public-ip>
Screenshot: Capture a screenshot of the webpage being served from the cloud VM.
6. Install PHP and MySQL on the VM
If PHP and MySQL are not already installed, run the following commands:

Install PHP:

bash
Copy code
sudo apt update
sudo apt install php libapache2-mod-php
Install MySQL:

bash
Copy code
sudo apt install mysql-server
7. Start MySQL Server and Login
Start the MySQL service:
bash
Copy code
sudo systemctl start mysql
Log in to MySQL as the root user:
bash
Copy code
sudo mysql -u root -p
8. Create Database, Table, and User
Inside the MySQL shell, run the following commands to create a database, table, and user:

Create Database:

sql
Copy code
CREATE DATABASE userdb;
USE userdb;
Create a Users Table:

sql
Copy code
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY, 
    username VARCHAR(50), 
    email VARCHAR(100), 
    password VARCHAR(255)
);
Screenshot: Capture a screenshot showing the creation of the database, table, and user in MySQL.

9. Create/Register a User via PHP Script
Write a PHP registration script that allows users to register with their username, email, and password. The data should be stored in the users table of the userdb database.
Ensure the form connects to the MySQL database and inserts data correctly.
Access the registration page from your browser:
bash
Copy code
http://<your-vm-public-ip>/register.php
10. Login as the Created User
After registering a new user, log in with the same credentials.
Screenshot: Capture a screenshot showing the successful login page.
11. Share the Public IP of Your Web Server
Share your web server’s public IP with friends or colleagues to verify if they can access the registration and login pages.
12. Public IP
The public IP of my VM: 98.70.101.125
