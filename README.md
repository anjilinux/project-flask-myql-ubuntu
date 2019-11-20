# Todo-flask-mysql
Example on how to set up a multi-containers platform using Python-Flask and MySQL database 

## How to set up the environment platform
Start a MySQL database container   
```code
docker run -d -it --name db -e MYSQL_ROOT_PASSWORD=password -p 3306:3306 \
-v /var/log/mysql-db:/var/log/mysql astondevops/docker-mysql-5.6
```
Launch a PhpMyAdmin container connected to the MySQL database
```code
docker run -d -it --name phpmyadmin --link db:mysql \
 -e MYSQL_USERNAME=root -p 8181:80 nazarpc/phpmyadmin
```
Get this repository  
```git clone https://github.com/system-dev-formations/todo-flask-mysql.git```
Build todo-sql image  
```cd todo-flask-mysql```
```docker build -t todo-sql . ```
In your Goland Intellij IDE set a connection to the MySQL database   
create a database     
and run the script ./sql/todos.sql 
After type in your shell console  
```code 
docker run -it --name todo --link db:todo -p 5000:5000 todo-sql
```
Bring up your favorite browser   
``` http://localhost:5000/```
and check 

