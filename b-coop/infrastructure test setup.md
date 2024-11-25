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

### Environment Variables

following envorinment variables are defined in ~/.profile
```
#
# upay.me environment
#

export UPAYMEHOME="$HOME"
export UPAYMEBIN="$UPAYMEHOME/bin"
export UPAYMEDEV="$UPAYMEHOME/dev"
export UPAYMETEST="$UPAYMEHOME/upaymetest"
export UPAYMEPROD="$UPAYMEHOME/upaymeprod"
export THOREGONGITROOT="$UPAYMEDEV"
export UPAYMEGITROOT="$UPAYMEDEV/thatsme/thoregon/easypay"

export UPAYMETESTCLI="$UPAYMETEST/cli"
export UPAYMETESTAGENTS="$UPAYMETEST/agent"
export UPAYMETESTMODULES="$UPAYMETESTAGENTS/modules"
export UPAYMETESTSITES="$UPAYMETESTAGENTS/caddy"
export UPAYMETESTWWW="$UPAYMETEST/www"
export UPAYMETESTPACKS="$UPAYMETESTWWW/dist"

export UPAYMEPRODCLI="$UPAYMEPROD/cli"
export UPAYMEPRODAGENTS="$UPAYMEPROD/agent"
export UPAYMEPRODMODULES="$UPAYMEPRODAGENTS/modules"
export UPAYMEPRODSITES="$UPAYMEPRODAGENTS/caddy"
export UPAYMEPRODWWW="$UPAYMEPROD/www"
export UPAYMEPRODPACKS="$UPAYMEPRODWWW/dist"

# export UPAYME_TEST=1
```

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
$ docker exec -ti <container1> ping <container2)    # check if container1 can reach container 2 
$ docker exec -ti <containername> ss -l             # list open ports from container

$ docker network instpect <networkname>
$ docker container instpect <containername>
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
$ docker network create --attachable upayme-net
$ docker network create --attachable upayme-test-net
```

CAUTION:
- containers within the network can be reached directly by the port they open from other containers in the network
- the mapped ports (e.g. in docker-compose.yml) can not be accessed from containers in the same network!

e.g. if there is a port mapping:
    ports:
        - 1234:5678
to check if a container can be reached:

```
docker exec caddy ping upaymetestupayme
```

the containers in the same docker network must open 5678 !

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

upay.me 
-------

upayme structure in HOME
```
dev                         git repos

~/upaymetest    ~/upaymeprod
    cli                     thoregon command line tools
        modules             module sources -> in ~/upaymetest/cli: ln -s ~/upaymetest/agent/modules/ modules, ln -s ~/upaymeprod/agent/modules/ modules
    agent                   
        caddy               caddy configs for agents (domains). name = caddy_<containername>
        modules             module sources -> target for copy modules from git 
        instances
            <containername>
                etc             agent config
                log             agent log
                data            agent data
    www                     copy files from /Client
        dist    
        .etc
            <containername>     caddy rewrite target for /etc/* for each container
        .pub 
            <containername>     caddy rewrite target for /pub/* for each container
```

### Scripts

```
~/.scripts
    makemodules.sh
    makewww.sh
    
# make executable
$ chmod +x * 
```

create symlinks
```
$ ln -s  /home/lucky/.scripts/makewww.sh /home/lucky/bin/makewww
...
```


Containers
----------

### Test
following test containers exist
- nexus     ... upayme nexus  
- upayme    ... upayme as vendor
- vendor    ... arbitrary test vendor

domains: 
- nexus.bernhard-lukassen.com
- upayme.bernhard-lukassen.com
- vendor.bernhard-lukassen.com


Create users:
```
// let ups = await app.current.services.nexus_upayme.consumer();
let ups = agent.current.consumer('upayme')

// upayme user, valid for upayme and nexus test: user: upayme@bernhard-lukassen.com, pwd: KH2VvSbky
await ups.createCard4SSI({ id: 'upayme', email: 'upayme@bernhard-lukassen.com', firstName: 'Test', lastName: 'Upayme', domain: 'upayme.bernhard-lukassen.com', company: 'upay.me', alias: 'upayme', salt: 'FCD889fxWTCtBGBG', anchor: 'GJB3qdeO2q8kllNOlvDDPa6xJi31Qtx4PH3NsckZ8aI1b7s0HX0SeVPLCSGsA6e8', password: 'KH2VvSbky' });
await ups.addVendorInstance({ vendorid, 'upayme', containername: 'upayme', domain: 'upayme.bernhard-lukassen.com', port: 30101, main: true });

// testvendor, valid for vendor test instane: user: vendor@bernhard-lukassen.com, pwd: 5lC5r1bS2
await ups.createCard4SSI({ id: 'vendor', email: 'vendor@bernhard-lukassen.com', firstName: 'Test', lastName: 'Vendor', domain: 'vendor.bernhard-lukassen.com', company: 'vendor', alias: 'vendor', salt: 'I0jJyyi68', anchor: 'RVgw3fIxTTbPsm9hnIWgAwwyuK1Y5cSRNVM9x2Em48YEDB8o4dcPDkzf6KVhN48T', password: '5lC5r1bS2' });
await ups.addVendorInstance({ vendorid, 'vendor', containername: 'vendor', domain: 'vendor.bernhard-lukassen.com', port: 30102, main: true });
```

### Prod
following production containers exist
- nexus     ... upayme nexus
- upayme    ... upayme as vendor

- erikawest  ... ernährenswert LLC
- vivian

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
**OLD**, not used anymore

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


# Containers
# - image upload server!
# - peerjs signaling server!

# network connects to external caddy_neuland!


UI uPayMe
-----------

UI webroots must be mapped in the 'docker-compose.yaml' as volume  
here are **all** docroots available as subdirectories

copy /Client content to ~/upaymetest/www and (after testing) ~/upaymeprod/www 
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
