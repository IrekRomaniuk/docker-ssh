http://www.inanzzz.com/index.php/post/qdil/creating-a-ssh-server-with-openssh-by-using-docker-compose-and-connecting-to-it-with-php
https://docs.docker.com/engine/examples/running_ssh_service/

```
docker build --no-cache -t debian-ssh .
docker run --rm -p 2222:22 debian-ssh
docker tag debian-ssh irom77/debian-ssh:latest
docker push irom77/debian-ssh
```

Test

Connection
```
$ ssh master@172.18.0.2 -p 22
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
