Java + maven:  
-----------

sudo apt update  
sudo apt install -y openjdk-17-jdk  
sudo apt install -y maven  
mvn clean install  
java -version  
mvn -version  

mvn spring-boot:run  

Node.js + npm:  
--------------

sudo apt install -y nodejs npm  
node -v  
npm -v  


MySql:  
------

sudo apt install -y mysql-server  
sudo systemctl start mysql  
sudo systemctl enable mysql  

sudo mysql  
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
FLUSH PRIVILEGES;
EXIT;

sudo mysql -u root -p
CREATE DATABASE quotes_app;  
USE quotes_app;  

Tables:
-----

CREATE TABLE users (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(50) UNIQUE NOT NULL,
    name VARCHAR(100),            -- Added comma
    password VARCHAR(100)         -- Added comma
);

CREATE TABLE quotes (             -- Named 'quote' to match your select
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    text VARCHAR(255),
    author VARCHAR(255),
    user_id BIGINT,
    created_at TIMESTAMP(6) DEFAULT CURRENT_TIMESTAMP(6), -- Added this!
    FOREIGN KEY (user_id) REFERENCES users(id)
);

INSERT INTO users (username, name, password) VALUES ('Surendra', '1234', '1234');  

INSERT INTO quote (text, author, user_id) VALUES ('The only way to do great work is to love what you do.', 'Steve Jobs', 1);  

sudo chown -R ubuntu:ubuntu /home/ubuntu/quote-new


Start:
-----

npm install  
npm start  

mvn clean isntall  
mvn spring-boot:run  
