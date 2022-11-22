## Install Docker MySQL & MyPhp Admin

Install Docker
```sh
sudo apt install docker.io
```
Install MySQL
```sh
sudo docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=mypass123 -d --restart always mysql
```
Install MyPHP Admin
```sh
sudo docker run --name phpmyadmin -d --link mysql:db -p 8081:80  --restart always phpmyadmin/phpmyadmin
```
Add user to MySQL
```
sudo docker exec -it mysql bash
```
```
mysql -u root -p
```
```
CREATE USER 'user1'@'%' IDENTIFIED BY 'user1@123';
GRANT ALL PRIVILEGES ON *.* TO 'user1'@'%';
FLUSH PRIVILEGES;
```
Export data from MySQL DB
```
sudo docker exec mysql mysqldump -u user1 -p"user1@123" test > test.sql
```
Import data to MySQL DB
```
docker exec -i mysql mysql -uuser1 -p'user1@123' <<<"CREATE DATABASE IF NOT EXISTS test;"
docker exec -i mysql mysql -uuser1 -p'user1@123' test < test.sql
```
