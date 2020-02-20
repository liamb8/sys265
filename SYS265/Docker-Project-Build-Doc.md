# Creating a Zabbix Network Monitor using Docker-Compose

1. Clone the github which the files are located at 
git clone https://github.com/zabbix/zabbix-docker
This will create a new directory called zabbix-docker which you will want to cd into for the next steps. 

2. Do git checkout trunk 
After this, you will want to make sure that you don't have any previous version of zabbix, mariadb, and httpd running otherwise it would mess with the installation process.
You can check this by doing ps | grep zabbix

3. Now run docker-compose -f docker-compose_v3_ubuntu_mysql_latest.yaml pull
This will now pull the files related to the yaml file using the docker-compose and it will install all the necessary requirements that Zabbix needs to run and set it up for you. During this process, there may be an error regarding Healthchecks not being supported. This can be fixed by editing the yaml file and commenting out the start_period section. 

4. docker-compose -f docker-compose_v3_ubuntu_mysql_latest.yaml up -d 
This will start all the necessary docker containers that Zabbix is using to run. 
After this go to the ip address of the machine that the docker-compose for Zabbix was installed on and you can log in with the default username of Admin and password of zabbix. During this process due to the large amount of containers zabbix uses to run it can take awhile for it to first load the webpage. 

# Customization of Docker Compose File
In the yaml file I increased the memory reservations from 256M to 512M and changed the stop_grace_period from 30 seconds to 60 seconds. 
