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
