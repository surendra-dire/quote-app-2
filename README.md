
# Quotes Management Application
A full-stack application featuring a Java Spring Boot backend, a React.js frontend, and a MySQL database.  

### Prerequisites & Environment Setup
Before running the application, ensure your system is updated and the required runtimes are installed.

#### Install Java & Maven
sudo apt update
sudo apt install -y  
openjdk-17-jdk maven  
java -version 
mvn -version 

### Install node js & npm  
sudo apt install -y nodejs npm  
node -v  
npm -v  

### Install and Configure MySQL Server  
sudo apt install -y mysql-server  
sudo systemctl start mysql  
sudo systemctl enable mysql  

### Root password setup
Switch MySQL from "system-login" to "password-login" (setting the password to root) so your Spring Boot app can connect. FLUSH PRIVILEGES saves these changes, and EXIT closes the database prompt  

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';  
FLUSH PRIVILEGES;  
EXIT;  

### create database and tables  
mysql -u root -p  
CREATE DATABASE quotes_app;  
USE quotes_app;  

-- Create Users Table  
CREATE TABLE users (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    name VARCHAR(100),
    password VARCHAR(100)
);

-- Create Quotes Table  
CREATE TABLE quotes (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    text VARCHAR(255),
    author VARCHAR(255),
    user_id BIGINT,
    created_at TIMESTAMP(6) DEFAULT CURRENT_TIMESTAMP(6),
    FOREIGN KEY (user_id) REFERENCES users(id)
);

-- Insert Initial Data  
INSERT INTO users (username, name, password) VALUES ('Surendra', 'Surendra Kumar', '1234');  
INSERT INTO quotes (text, author, user_id) VALUES ('The only way to do great work is to love what you do.', 'Steve Jobs', 1);  

# 🚀 **Getting Started**

Permissions  
Ensure the current user owns the project directory so you don't run into "Permission Denied" errors:  
sudo chown -R $USER:$USER /home/ubuntu/quote-app 

Navigate to your backend and run:  
mvn clean install  
mvn spring-boot:run  

Navigate to your frontend directory and run:  
npm install  
npm start  

### Troubleshoot commands  
sudo ufw allow 8080  
sudo netstat -tulpn | grep 8080  
sudo systemctl status mysql  
sudo kill -9 $(sudo lsof -t -i:8080) or sudo ss -lptn 'sport = :8080'  
