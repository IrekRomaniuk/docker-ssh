http://www.inanzzz.com/index.php/post/qdil/creating-a-ssh-server-with-openssh-by-using-docker-compose-and-connecting-to-it-with-php
https://docs.docker.com/engine/examples/running_ssh_service/

```
dos2unix *.sh
export SSH_MASTER_USER=azureuser
export SSH_MASTER_PASS=azurepass
docker build --no-cache -t docker-ssh . --build-arg SSH_MASTER_USER=azureuser --build-arg SSH_MASTER_PASS=azurepass
docker run --rm -p 2222:22 docker-ssh
docker tag docker-ssh irom77/docker-ssh:latest
docker push irom77/docker-ssh
```

Test

Connection
```
$ ssh master@localhost -p 22 -o StrictHostKeyChecking=no
master@server:~$
```
Create a new user
```
master@server:~$ sudo useradd -m -d /home/inanzzz inanzzz -s /bin/bash
master@server:~$ echo "inanzzz:inanzzz" | sudo chpasswd
```
Test new user login
```
$ ssh inanzzz@172.18.0.2 -p 22
inanzzz@server:~$
```
