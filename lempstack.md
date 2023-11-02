![image](https://github.com/kennyanju/lempstack/assets/10983149/0b354ac8-eac5-4086-9fc9-48f3922ea0ee)
 


chmod 400 /Users/sadiqadeyanju/Downloads/dareiolempstack.pem

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/a22e7071-6e8b-49c3-a689-7cac96c334ae)



ssh -i /Users/sadiqadeyanju/Downloads/dareiolempstack.pem -v ubuntu@ec2-18-130-229-53.eu-west-2.compute.amazonaws.com

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/af879834-80a9-43ae-9f0e-bd9b192f4389)


$ sudo apt update


![image](https://github.com/kennyanju/lempstack/assets/10983149/9772c0cd-115b-46c8-b3ee-9b8c3a1481e0)



 

$ sudo apt upgrade
![image](https://github.com/kennyanju/lempstack/assets/10983149/6f7b6d00-419c-4bc4-a787-892d11a3090f)

 

$ sudo apt install nginx

![image](https://github.com/kennyanju/lempstack/assets/10983149/0821065d-1679-476b-9c6b-626ee936f34a)

 



$ sudo systemctl status nginx

 


curl http://localhost:80

 


http://ec2-18-130-229-53.eu-west-2.compute.amazonaws.com/

 
$ sudo apt install mysql-server

 


$ sudo mysql

 


ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';

 


Exit

 

$ sudo mysql_secure_installation 


 

$ sudo mysql -p

 

mysql> exit

 

$ sudo apt install php-fpm php-mysql

 

$ sudo mkdir /var/www/projectLEMP

$ sudo chown -R $USER:$USER /var/www/projectLEMP

$ sudo nano /etc/nginx/sites-available/projectLEMP

 

$ sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
$ sudo nginx -t
 

$ sudo unlink /etc/nginx/sites-enabled/default

$ sudo systemctl reload nginx

$ sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html

 


$ nano /var/www/projectLEMP/info.php

 

http://ec2-18-130-229-53.eu-west-2.compute.amazonaws.com/info.php

 

$ sudo rm /var/www/projectLEMP/info.php

$ sudo mysql -u root -p







 


mysql> CREATE DATABASE `example_database`;

mysql>  CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 
'PassWord.1';

mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';

 

mysql> exit

$ mysql -u example_user -p


 

mysql> SHOW DATABASES;
 

CREATE TABLE example_database.todo_list (item_id INT AUTO_INCREMENT,content VARCHAR(255),PRIMARY KEY(item_id));

mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");

mysql>  SELECT * FROM example_database.todo_list;

 

$ nano /var/www/projectLEMP/todo_list.php

 


 
![image](https://github.com/kennyanju/lempstack/assets/10983149/b7cacc27-fa41-4e86-89ff-bb1d65e878fd)
