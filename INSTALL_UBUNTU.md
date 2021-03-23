# Install on Ubuntu

## Pre-requisites
```shell script
sudo ufw disable
sudo apt-get -y install python3 python3-venv
python3 -m venv venv
source venv/bin/activate 
sudo apt-get -y install build-essential
sudo apt-get install python3-dev libxml2-dev libxslt-dev
pip3 install docker-compose
````
Note: ssh tunnel ```ssh -L 3306:localhost:11000  ubuntu@54.32.22.22```

Add this command in mysql   
Get your public ip address   
https://www.showmyip.com/  
```GRANT ALL ON foo.* TO bar@'public-ip-address' IDENTIFIED BY 'password';```