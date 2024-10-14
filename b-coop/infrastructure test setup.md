Server
======

Neuinstallation:
S4 (b-coop)
185.11.139.203  fe80::216:ff:fe00:9861
Ubuntu 22.04 LTS "Jammy Jellyfish"

User
----
id: lucky
pwd: d2GD1@b$
pubkey:
    ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDNBcRTtiFmdmmK5yK0WgTIa4Ze7+odug+g+qLEsRDq7Odim5RFOIA53AbH0bHW7GPuSrRvigLYZv802nZryO5nwplPdVhWbR5M7Z99WJPSbcJsVpXpOi5hXzNgmv7RnvksHnqBazi/DbMajHCZA0xD32OFHKyJatWz2a+nn2oNeQS978VJvl9HCANVqABH2w0ciPgcIlJpqyn6Gu6X1E34N+22KuU/IOa01WSkXzMICJ3nL77Xq9BRPo1bYX/JFtTYG19LQdeWc16mel7wBxZjhjPby+azQdF+62D4m+id3sSrQ4Af6e/sTFwA9imcyPw3ptNEHVYuuJc8AP+j7FrD bl@bernhard-lukassen.com

! no password login, only with keypairs

root
----
M17ytl$6m


Infrastructure
--------------

    # First!
    > sudo apt update
    # eventually
    > sudo apt upgrade -y


- mc (MidnightCommander)

```
$ sudo install mc -y
```

- sshd
    - https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-22-04
    - ports:

```
$ sudo vi /etc/ssh/sshd_config
#    Port 22
#    Port 2022
$ sudo systemctl restart ssh.service
```

- ufw
    - https://www.digitalocean.com/community/tutorials/ufw-essentials-common-firewall-rules-and-commands
    - https://phoenixnap.com/kb/configure-firewall-with-ufw-on-ubuntu

```
$ sudo apt install -y ufw
$ sudo ufw allow ssh
$ sudo ufw allow 2022/tcp
$ sudo ufw allow http
$ sudo ufw allow https
$ sudo ufw allow 9000/tcp  # peerjs signaling server
$ sudo ufw allow 8000/tcp  # portainer tunnel server

$ sudo ufw enable
$ sudo ufw status numbered

$ sudo ufw delete <num>
```

  - docker
      - https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-22-04

```
$ sudo apt update
$ sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
$ sudo apt update
$ apt-cache policy docker-ce
$ sudo apt install -y docker-ce
$ sudo systemctl status docker
# add your username to the docker group (logout/login to have it effective)
$ sudo usermod -aG docker ${USER}

# join shell of a running container
$ docker exec -it <container_name> sh

# info
$ docker compose ls                     # list available compose projects with status
$ docker image ls                       # list images
$ docker image rm <imagename>           # remove image, not auto by docker compose down, must be made manually
$ docker container ls                   # list containers
$ docker container rm <containername>   # remove container (auto by docker compose down)
$ docker network ls                     # list networks
$ docker network rm <networkname>       # remove network (auto by docker compose down)
$ docker logs <containername> | more    # show logs of a container
```


- docker compose
    - https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-22-04
    - https://www.youtube.com/watch?v=DM65_JyGxCo

```
$ mkdir -p ~/.docker/cli-plugins/
$ curl -SL https://github.com/docker/compose/releases/download/v2.3.3/docker-compose-linux-x86_64 -o ~/.docker/cli-plugins/docker-compose
$ chmod +x ~/.docker/cli-plugins/docker-compose
$ docker compose version
```

- node environments
    - https://tecadmin.net/how-to-install-nvm-on-ubuntu-22-04/

```
# nvm
$ curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash

# node
$ nvm install 18.7.0

# node gyp
$ npm i -g node-pre-gyp
```

DNS
---

define following subdomains:
- portainer.bernhard-lukassen.com
- portainer.thoregon.io
- resource.thoregon.io/

    A       185.11.139.203
    AAAA    fe80::216:ff:fe00:9861

Network
-------
define a common docker network
```
$ docker network create upayme-net
```
Use in docker-compose.yml
```
services:
  service1:
    image: myimage
    networks:
      - upayme-net

networks:
  upayme-net:
    external: true
```



Containers
----------

-> https://towardsdatascience.com/the-complete-guide-to-docker-volumes-1a06051d2cce

# Join docker container shell
# - start any container installed shell
# - get name from > docker ps
```
> docker exec -it <container_name> sh
```

- make directory for caddy container (change useranme!)
    > mkdir -p /home/lucky/containers/caddy
    - copy 'Caddyfile'
    ! CAUTION: the port in Caddyfile directly maps the the port in the container (9000), not to the forwarded port (9010)
- make directory for caddy compose (change useranme!)
    > mkdir -p /home/lucky/compose/caddy
    - copy caddy_portainer 'docker-compose.yaml'
- make directory for portainer container (change useranme!)
    > mkdir -p /home/lucky/containers/portainer

  -> https://portainer.bernhard-lukassen.com/

- reverse proxy (caddy) with portainer
    - setup with network and portainer
        - https://gist.github.com/BlueHippoGithub/1a6b6569cea8520ea5b6119e8877c70a (edit)
        - https://www.youtube.com/watch?v=qj45uHP7Jmo

```
> cd ~/compose/caddy
> docker compose up -d
```

- peerjs signaling server
  - compose/peerjssignalin  
  - docker compose up -d

(previous: > docker run --name peer-signaling -p 9000:9000 -d peerjs/peerjs-server)


Resource Server
---------------

- copy testresourceserver -> /home/lucky/compose/resourceserver
  - https://resource.thoregon.io

```
$ mkdir -p /home/lucky/containers/resourceserver/www
$ cd /home/lucky/compose/resourceserver
$ docker compose build
$ docker compose up -d
```

todo:
    - add domain 'resource.thoregon.id'
    - Caddyfile
    - mod docker-compose.yml
        - join network caddy_neuland
    - ufw delete rules for 7779

join container bash
```
$ docker exec -it <containerid> bash
```

Thoregon
--------


Containers
- image upload server!
- peerjs signaling server!

- copy stripecollector -> /home/lucky/compose/stripecollector
# network connects to external caddy_neuland!

```
$ mkdir -p /home/lucky/containers/stripecollector/data
$ sudo chown -R root:root /home/lucky/containers/stripecollector/data
```
- !! copy neuland.tdb -> /home/lucky/containers/stripecollector/data

```
$ mkdir -p /home/lucky/containers/stripecollector/.thoregon
$ sudo chown -R root:root /home/lucky/containers/stripecollector/.thoregon

$ cd /home/lucky/compose/stripereceiver
$ docker compose build
$ docker compose up -d
```

UI uPayMe
-----------

UI webroots must be mapped in the 'docker-compose.yaml' as volume  
here are **all** docroots available as subdirectories 
````
volumes:
  ....
  - /home/lucky/www:/www
````
use in Caddyfile  
map the subdirectory of the docroot to the domain  
also rewrite the config files to the vendors config
````
upayme.thoregon.io {
    root * /www/upaymeui
    rewrite universe.prod.mjs .cust/<vendorid>/universe.prod.mjs      # config for domain
    file_server
    handle_errors {
        rewrite * /404-notfound.html
        file_server
    }
}
````

Vendor uPayMe SA
----------------

UI Admin uPayMe
---------------

Admin uPayMe SA
---------------


Production (Part 2)
===================

**HashiCorp**
- terraform
- consul
- vault
- nomad
    > sudo apt install -y nomad
