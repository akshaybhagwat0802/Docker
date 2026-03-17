## Setting up the Mariadb database 
### 1) launch an ec2 instance having ubuntu images.
#### i) connect to that instance .
### 2) create an databse --> (Aurora and rds).
### 3) After connection used that commmands 
i) switch  to the root user and update the terminal 
```bash
sudo -i
&& sudo apt update
```
ii) Install the mysql server on server.
```bash
sudo apt install mysql-client -y
```
iii) login to the mysql
```bash
mysql -h <rds endpoint> -u<username> -p<password>
```
iv) create student database 
```bash
CREATE DATABASE student_db;
GRANT ALL PRIVILEGES ON springbackend.* TO 'username'@'localhost' IDENTIFIED BY 'your_password';
```
v) connect to that database 
```bash
USE student_db;
```
vi) create table in database 
```bash
CREATE TABLE `students` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `name` varchar(255) DEFAULT NULL,
  `email` varchar(255) DEFAULT NULL,
  `course` varchar(255) DEFAULT NULL,
  `student_class` varchar(255) DEFAULT NULL,
  `percentage` double DEFAULT NULL,
  `branch` varchar(255) DEFAULT NULL,
  `mobile_number` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=80 DEFAULT CHARSET=latin1 COLLATE=latin1_swedish_ci;
```
vii) Exit the terminal 
```bash
Exit;
```
