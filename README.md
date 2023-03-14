# Workpress_and_AWS

Project = Deploy Workpress Website on AWS 

    -In this project we will deploy workpress website on AWS. We have two ways to complete this task. 
    -One is treditional way by doing each task one by one and another one by AWS EC2 User data method. Where we can write each command and with single click      we can deploy it easily. 
    - We also have simple way to deploy workpress by AWS Lightsail.
    - Following steps and commands are useful to deploy workpress website on AWS.

Architecture for this Project = 
Pushed in Image form.

Method 1 = 
Create Workpress with AWS Lightsail. 

Method 2 = 
Create EC2 instance and open it in MobaXterm or RDP. Follow each and every step to complete the task. Following method 2 commands are neceesary to do it. 

Method 3 =
#!/bin/bash

# Update and upgrade packages
apt update && apt upgrade -y

# Install Apache
apt install apache2 -y

# Verify Apache is running
systemctl status apache2

# Install MariaDB
apt install mariadb-server mariadb-client -y

# Secure the MariaDB installation
mysql_secure_installation

# Install PHP and PHP-MySQL
apt install php php-mysql -y

# Create a database and user for WordPress
mysql -u root -p <<EOF
CREATE DATABASE wordpress_db;
CREATE USER 'Shivam_user'@'localhost' IDENTIFIED BY 'Shiv123';
GRANT ALL ON wordpress_db.* TO 'Shivam_user'@'localhost' IDENTIFIED BY 'Shiv123';
EXIT;
EOF

# Download and extract WordPress
cd /tmp && wget https://wordpress.org/latest.tar.gz
tar -xvf latest.tar.gz

# Copy WordPress files to the web server directory
cp -R wordpress /var/www/html/

# Set permissions for WordPress files
chown -R www-data:www-data /var/www/html/wordpress/
chmod -R 755 /var/www/html/wordpress/

# Create uploads directory for WordPress
mkdir /var/www/html/wordpress/wp-content/uploads
chown -R www-data:www-data /var/www/html/wordpress/wp-content/uploads/

