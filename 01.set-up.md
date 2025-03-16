# Start mysql

```bash
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=pass -p 3306:3306 -v /var/lib/mysql -d mysql:latest
c75137145ee4114a8862d29b574105838cde576a23c3e09a69e2b187eee8f2f6
                                                                                                                                 
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ 
```

# List containers running

```bash
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ docker ps                                                                                                   
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                                  NAMES
c75137145ee4   mysql:latest   "docker-entrypoint.s…"   52 seconds ago   Up 52 seconds   0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql-container
                                                                                                                                 
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ 
```

# Stop the container (but not remove the container)

```bash
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ docker stop mysql-container
mysql-container
                                                                                                                                                      
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ 
```

# Make sure the container is stopped

```bash
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ docker ps                  
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
                                                                                                                                                      
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ 
```

# Next time, just start the container (do not need to create new container)
# Because data is persistet (by using -v)

```bash
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ docker start mysql-container
mysql-container
                                                                                                                                                      
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ 
```

# Check if the container is running again

```bash
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ docker ps                   
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS          PORTS                                                  NAMES
c75137145ee4   mysql:latest   "docker-entrypoint.s…"   6 minutes ago   Up 33 seconds   0.0.0.0:3306->3306/tcp, :::3306->3306/tcp, 33060/tcp   mysql-container
                                                                                                                                                      
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ 
```

# Check mysql version

```bash
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ docker exec mysql-container mysql --version
mysql  Ver 9.2.0 for Linux on x86_64 (MySQL Community Server - GPL)
                                                                                                                                                      
(base) ┌──(klx㉿kali)-[~/learn-mysql-workbench]
└─$ 
```

# Open MySQL Workbench and connect using these properties

```yaml
Connection Method: Standard (TCP/IP)
Hostname: localhost
Port: 3306
Username: root
Password: pass
```

# Tips

Change `mysql:latest` image with the specific version that compatible with MySQL Workbench.
For example: For MySQL Workbench version 8.0, use docker image `mysql:8.0`