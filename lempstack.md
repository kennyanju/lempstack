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

 
![image](https://github.com/kennyanju/lempstack/assets/10983149/de3fe930-d93d-46f2-8313-0972a9dc8079)


curl http://localhost:80

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/976c4591-4796-4877-83aa-0dafc8e662b5)



http://ec2-18-130-229-53.eu-west-2.compute.amazonaws.com/

![image](https://github.com/kennyanju/lempstack/assets/10983149/009caa98-260b-4e32-bff2-16df5a008bf6)


 
$ sudo apt install mysql-server

 
![image](https://github.com/kennyanju/lempstack/assets/10983149/94976e01-48b8-413e-89b5-c2f304c1ed70)


$ sudo mysql

 
![image](https://github.com/kennyanju/lempstack/assets/10983149/c930f7cd-f752-40bd-84ab-84ebaac95f45)


ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/bc441d83-c7e4-4ea2-847a-e3a4295c8405)



Exit

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/a2e0dc24-e238-4122-9af4-56f208d0095e)


$ sudo mysql_secure_installation 


 ![image](https://github.com/kennyanju/lempstack/assets/10983149/10deb69b-b8a2-4f8b-a3f6-48d70bdb1ca8)


 ![image](https://github.com/kennyanju/lempstack/assets/10983149/e7883964-a2fb-4ae7-a6c5-64f57f85d1f3)



$ sudo mysql -p

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/ba4572c7-083c-40db-b99a-a5fa66c1f839)


mysql> exit

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/98a4c837-6e9a-41ab-a4ba-ede821fa2b22)


$ sudo apt install php-fpm php-mysql

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/30a80e2c-1ddd-46b6-92d5-dc013546e1be)


$ sudo mkdir /var/www/projectLEMP

$ sudo chown -R $USER:$USER /var/www/projectLEMP

$ sudo nano /etc/nginx/sites-available/projectLEMP

![image](https://github.com/kennyanju/lempstack/assets/10983149/c8b95b3f-e2ca-49b1-a0da-1329b7e11b9c)
 

$ sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
$ sudo nginx -t
 
![image](https://github.com/kennyanju/lempstack/assets/10983149/aad06f95-2930-47fc-8ab6-c369e8817f24)


$ sudo unlink /etc/nginx/sites-enabled/default

$ sudo systemctl reload nginx

$ sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html


 ![image](https://github.com/kennyanju/lempstack/assets/10983149/01799293-ec83-4930-baa7-a3919c7948d0)



$ nano /var/www/projectLEMP/info.php

![image](https://github.com/kennyanju/lempstack/assets/10983149/6f9345cc-09a1-43d8-b698-d1dce3f916ce)
 

http://ec2-18-130-229-53.eu-west-2.compute.amazonaws.com/info.php

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/47eeaee8-5770-475d-8a71-adbe6154f0cd)


$ sudo rm /var/www/projectLEMP/info.php

$ sudo mysql -u root -p



![image](https://github.com/kennyanju/lempstack/assets/10983149/390ea438-8467-46fc-86d2-82af4cf36d2d)




 


mysql> CREATE DATABASE `example_database`;

mysql>  CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 
'PassWord.1';

mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/e8c2456d-2cb1-42c0-be4b-90076fae5c60)


mysql> exit

$ mysql -u example_user -p


 ![image](https://github.com/kennyanju/lempstack/assets/10983149/6b2d93ae-fa82-4c4d-ad23-8fef2ad93a06)


mysql> SHOW DATABASES;
 
![image](https://github.com/kennyanju/lempstack/assets/10983149/9d33a6e8-e280-416d-9fd8-10af7d86add4)


CREATE TABLE example_database.todo_list (item_id INT AUTO_INCREMENT,content VARCHAR(255),PRIMARY KEY(item_id));

mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");

mysql>  SELECT * FROM example_database.todo_list;

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/02aa0396-44ac-4649-8930-e17df47b7a61)


$ nano /var/www/projectLEMP/todo_list.php

 ![image](https://github.com/kennyanju/lempstack/assets/10983149/0ad2a5ef-2370-4ce0-845b-0fb7331a9710)

