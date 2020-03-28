

### 查找mysql镜像

```bash
➞  docker search mysql                                                         
NAME                              DESCRIPTION                                     STARS               OFFICIAL            AUTOMATED
mysql                             MySQL is a widely used, open-source relation…   8719                [OK]                
mariadb                           MariaDB is a community-developed fork of MyS…   3049                [OK]                
mysql/mysql-server                Optimized MySQL Server Docker images. Create…   645                                     [OK]
centos/mysql-57-centos7           MySQL 5.7 SQL database server                   63                                      
centurylink/mysql                 Image containing mysql. Optimized to be link…   61                                      [OK]
mysql/mysql-cluster               Experimental MySQL Cluster Docker images. Cr…   54                                      
deitch/mysql-backup               REPLACED! Please use http://hub.docker.com/r…   41                                      [OK]
bitnami/mysql                     Bitnami MySQL Docker Image                      36                                      [OK]
tutum/mysql                       Base docker image to run a MySQL database se…   34                                      
schickling/mysql-backup-s3        Backup MySQL to S3 (supports periodic backup…   28                                      [OK]
prom/mysqld-exporter                                                              23                                      [OK]
linuxserver/mysql                 A Mysql container, brought to you by LinuxSe…   22                                      
centos/mysql-56-centos7           MySQL 5.6 SQL database server                   16                                      
circleci/mysql                    MySQL is a widely used, open-source relation…   15                                      
mysql/mysql-router                MySQL Router provides transparent routing be…   13                                      
arey/mysql-client                 Run a MySQL client from a docker container      11                                      [OK]
imega/mysql-client                Size: 36 MB, alpine:3.5, Mysql client: 10.1.…   8                                       [OK]
openshift/mysql-55-centos7        DEPRECATED: A Centos7 based MySQL v5.5 image…   6                                       
yloeffler/mysql-backup            This image runs mysqldump to backup data usi…   6                                       [OK]
fradelg/mysql-cron-backup         MySQL/MariaDB database backup using cron tas…   4                                       [OK]
ansibleplaybookbundle/mysql-apb   An APB which deploys RHSCL MySQL                2                                       [OK]
genschsa/mysql-employees          MySQL Employee Sample Database                  2                                       [OK]
jelastic/mysql                    An image of the MySQL database server mainta…   1                                       
monasca/mysql-init                A minimal decoupled init container for mysql    0                                       
widdpim/mysql-client              Dockerized MySQL Client (5.7) including Curl…   0                                       [OK]


```

### 拉取镜像

```bash
➞  docker pull mysql
```

### 运行容器

```bash
➞  docker run -p 3306:3306 --name mysql -v $PWD/conf:/etc/mysql/conf.d -v $PWD/logs:/logs -v $PWD/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql
```

