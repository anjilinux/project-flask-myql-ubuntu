# Todo-flask-mysql
Example on how to set up a multi-containers platform using Python-Flask and MySQL database 

## How to set up the environment platform
Start a MySQL database container   
```shell script
docker run -d --name dbm -e MYSQL_ROOT_PASSWORD=password -p 3306:3306 \
-v /var/log/mysql-db:/var/log/mysql astondevops/docker-mysql-5.6
```
In your Goland Intellij IDE set a connection to the MySQL database   
create a database named ```tododb```      
and run the script ./sql/todos.sql   

Launch a PhpMyAdmin container connected to MySQL database
```shell script
docker run -d  --name phpmyadmin --link dbm:mysql \
 -e MYSQL_USERNAME=root -p 8181:80 nazarpc/phpmyadmin
```
Get this repository  
```git clone https://github.com/system-dev-formations/todo-flask-mysql.git```  
Build todo-sql image  
```cd todo-flask-mysql```  
```docker build -t todo-mysql . ```  
  
After type in your shell console  
```code 
docker run -d -it --name mytodo --link dbm:todo -p 26000:5000 todo-mysql
```

# Test
Bring up your favorite browser   
``` http://localhost:5000/```
and check 

# Docker-compose version 
We are going to setup a python virtualenv 
## On ubuntu
### Packages, virtualenv, activate  
```code
sudo apt-get -y install python3
sudo apt-get -y install python3-pip
sudo apt-get -y install python3-venv
python3 -m venv venv
source venv/bin/activate
```
### docker-compose set up
```code 
pip3 install wheel
pip3 install docker-compose
```
## On Centos
```code 
sudo yum install python3
sudo yum install python3-pip
python3 -m venv venv
source venv/bin/activate
pip3 install docker-compose
pip3 install --upgrade pip
```
## Execute
In the directory todo-flask-mysql, hit   
```docker-compose up ```  
or  
```docker-compose up -d```


