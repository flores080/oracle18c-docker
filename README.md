# Oracle 18c - Docker

Install docker

```bash
# UPDATE
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates -y
# ADD KEY
sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

sudo echo deb https://apt.dockerproject.org/repo ubuntu-xenial main >> /etc/apt/sources.list.d/docker.list

# INSTALLING
sudo apt-get update
sudo apt-get purge lxc-docker
sudo apt-get install linux-image-extra-$(uname -r) -y
sudo apt-get install docker-engine cgroup-lite apparmor -y
sudo usermod -a -G docker $USER

#TESTING
sudo service docker start
sudo docker run hello-world
```

Install Oracle DB

```bash
sudo docker pull dockerhelp/docker-oracle-ee-18c
sudo docker run -it dockerhelp/docker-oracle-ee-18c -p 1521:1521 
sudo sh post_install.sh
```

Create User

user: sys as sysdba

pass: oracle

```bash
sqlplus
```

```sql
SQL> alter session set "_ORACLE_SCRIPT"=true;
SQL> create user TEST identified by 1234;
SQL> grant dba to TEST;
```

https://soajp.blogspot.com/2019/03/instalar-oracle-database-18c-con-docker.html
