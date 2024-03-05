Infrastructure
==============

## Software

### Container

Thoregon
- GUN Relay (..../gun/examples/http.js)     (see: wss://matter.thoregon.io)
- OIDC SIOP     (https://openid.net/specs/openid-connect-self-issued-v2-1_0.html)
    - OpenID Provider for existing and other legacy services 

--> [storj](https://www.storj.io/)

### Pack Deploy Test

- [Kamal](https://kamal-deploy.org/)  Depoly apps
- [Turbopack](https://turbo.build/pack)  App packer
- [Devpod](https://devpod.sh/) Dev environments in a container, use anywhere
  - https://devpod.sh/docs/what-is-devpod

### System

- [Hashicorp](https://www.hashicorp.com/)
  - https://github.com/hashicorp
  - [Terraform](https://www.terraform.io/)
    - https://www.heise.de/hintergrund/Modularisierte-Infrastructure-as-Code-in-Terraform-9629194.html
  - [Nomad](https://www.nomadproject.io/) -> USE!
    - https://www.youtube.com/watch?v=SSfuhOLfJUg
      - https://github.com/schmichael?tab=repositories&q=nomad&type=&language=&sort=
    - https://www.youtube.com/watch?v=6GShFLUcdUA
  - [Consul](https://www.consul.io/)
  - [Vault](https://www.vaultproject.io/)
- [Kubernetes](https://kubernetes.io/) -> don't use!
    - https://kubernetes.io/docs/home/
    - https://github.com/godaddy/kubernetes-client
    - https://github.com/kubernetes-client/javascript/tree/master/examples
    - Kubernetes Automation: https://www.kubermatic.com/
      - https://github.com/kubermatic/kubeone
    - https://computerwelt.at/knowhow/13-tools-die-kubernetes-besser-machen/
    - https://www.heise.de/ratgeber/Kubernetes-lernen-und-verstehen-Teil-1-Cluster-aus-drei-Linux-Servern-bauen-7308546.html?wt_mc=intern.red.plus.newsticker.7-tage-news.teaser.teaser
    - ! https://www.redhat.com/sysadmin/compose-kubernetes-podman
    - install:
        - https://www.youtube.com/watch?v=uUupRagM7m0&list=PL2We04F3Y_41jYdadX55fdJplDvgNGENo
        - https://www.youtube.com/watch?v=UWg3ORRRF60
    - Select CNI
        - https://platform9.com/blog/the-ultimate-guide-to-using-calico-flannel-weave-and-cilium/
    - Persistent Storage
        - https://www.youtube.com/watch?v=X1FiU-6SwDc
        - https://www.youtube.com/watch?v=-hX1cqs4K68
    - Reverse Proxy
        - How to scale docker containers using Nginx as reverse proxy and load balancer
            -> https://www.youtube.com/watch?v=9aOpRhm33oM
        - https://www.youtube.com/watch?v=spbkCihFpQ8
- [Ansible](https://www.ansible.com/) Automation for everyone
  - Event-Driven Ansible
    - https://www.redhat.com/en/technologies/management/ansible/event-driven-ansible
    - https://www.heise.de/select/ix/2023/10/2316607093159260949)
- [Podman](https://podman.io/)
    - https://docs.podman.io/en/latest/Commands.html
- [Prometeus](https://prometheus.io/) Appliance Monitoring    
- [Grafana](https://grafana.com/) UI for monitoring
- [Nagios](https://www.nagios.org/) Network Monitoring
- [Nginx](https://www.nginx.com/) HTTP Proxy
    - [Nginx Proxy Manager](https://nginxproxymanager.com/guide/)
        - https://www.youtube.com/watch?v=aRURfnY2ikg
          - https://www.youtube.com/watch?v=B40TQcOzsNU
        - https://github.com/NginxProxyManager/nginx-proxy-manager
        - https://www.nginx.com/products/nginx/live-activity-monitoring/
        - https://github.com/schenkd/nginx-ui
- [Proxmox](https://www.proxmox.com/de/) Open Source Infrastucture
- [IPFS Container](https://docs.ipfs.io/how-to/run-ipfs-inside-docker/#set-up)
    - https://hub.docker.com/r/ipfs/go-ipfs/
    - https://cluster.ipfs.io/documentation/guides/k8s/
    - https://medium.com/rahasak/deploy-ipfs-cluster-with-kubernetes-c4cd8d64b7c8
- [ZeroMQ](https://zeromq.org/)
  - Container for SA to communicate with services
- Not now --> [Ceph](https://docs.ceph.com/en/quincy/)  Cluster File System/Object Store
    - https://www.linux-magazin.de/ausgaben/2019/12/rook-2/
    - https://www.digitalocean.com/community/tutorials/how-to-set-up-a-ceph-cluster-within-kubernetes-using-rook
    - https://medium.com/@adam.goossens/so-you-want-to-build-a-ceph-cluster-7ff9a033411d
    - https://www.storage-insider.de/was-ist-ein-ceph-cluster-a-1038874/
    - https://docs.ceph.com/en/latest/cephfs/quota/  
- DNS Providers
    - world4you
        - https://github.com/NerLOR/World4YouApi
        - https://www.world4you.com/faq/de/domains/faq.dns-verwaltung-kundenbereich.html

- [Swag](https://docs.linuxserver.io/general/swag)
- [Caddy](https://caddyserver.com/)
  - https://caddyserver.com/docs/quick-starts/reverse-proxy
  - https://www.youtube.com/watch?v=qj45uHP7Jmo
- [Traefik](https://doc.traefik.io/traefik/getting-started/quick-start/)


## Provisioning

Access Docker API:
- https://agustincb.github.io/docker-api
- https://github.com/apocas/dockerode-compose

## WebRTC
- https://stackoverflow.com/questions/54766128/can-a-pwa-run-a-webrtc-connection-in-the-background
- https://github.com/w3c/ServiceWorker/issues/1522
- WebRTC in Serviceworkers https://www.google.com/search?q=serviceworker+webrtc&oq=serviceworker+webrtc&aqs=chrome..69i57j0i13i19i512.6447j0j1&sourceid=chrome&ie=UTF-8
Containers
- https://idomagor.medium.com/how-to-dockerize-a-rtc-app-or-service-41368ea7b31
- https://habr.com/en/companies/flashphoner/articles/562244/
- https://hub.docker.com/r/spreed/webrtc/

## Authentication
- 
- [keycloak](https://www.keycloak.org/)
- [Authelia](https://www.authelia.com/)
- [Bitwarden](https://bitwarden.com/de-DE/)

### DevOps
- [FLUX](https://github.com/fluxcd/flux2) deploy to Kubernetes Clusters
- [Krius](https://github.com/infracloudio/krius) manage Prometheus, Thanos & friends across multiple clusters easily for scale
    - https://www.infracloud.io/blogs/krius-accelerating-monitoring-adoption/
        
Info:
- https://logz.io/blog/prometheus-vs-nagios-metrics/
- https://www.educba.com/prometheus-vs-nagios/
- https://www.metricfire.com/blog/prometheus-vs-nagios/

## VPN & DDNS

- https://timknowsbest.com/free-dynamic-dns
    - https://github.com/timothymiller/cloudflare-ddns

## V Server

- https://vergleich.focus.de/artikel/die-besten-vserver-im-vergleich_194211
- https://www.hosttest.de/vergleich/vserver.html

### Anbieter

- Google Kubernetes Engine
   - https://cloud.google.com/kubernetes-engine?hl=de
   - https://www.heise.de/news/Kosten-der-Google-Kubernetes-Engine-vorab-berechnen-zumindest-grob-7120708.html

- Managed Kubernetes
  - https://www.syseleven.de/produkte-services/kubernetes/
  - https://www.syseleven.de/metakube-testen/

- https://www.netcup.de/vserver/vps.php -> 40,80TB Traffic
- https://www.hosteurope.de/
    - https://www.hosteurope.de/Server/Virtual-Server/  -> Unlimited Traffic?
- https://www.hetzner.com/de/cloud  -> 20TB Traffic
    - https://www.hetzner.com/storage/storage-box   --> 
- https://www.hosting.de/
    - https://www.hosting.de/server/ -> 5TB Traffic
- https://www.ionos.de/
    - https://www.ionos.de/server/vps#tarife     -> Unlimited Traffic?
    - https://www.ionos.at/

- https://aws.amazon.com/de/lightsail/

## Mailserver

- https://www.heise.de/ratgeber/Mailserver-in-Eigenregie-Was-Sie-heute-brauchen-9329490.html?wt_mc=intern.red.plus.newsticker.7-tage-news.teaser.teaser

## Terminal Server (Linux)

- https://www.youtube.com/watch?v=sAllRma_0xc

## Test

BL Signal Client for testing

Mac:
    $ ssh s4 -L 9001:185.11.139.203:9001

Server: s4

    $ podman run --name signal-api -d -p 9001:8080 -v /opt/signal/bl:/home/.local/share/signal-cli --env-file /opt/signal/etc/signal-api-env docker.io/bbernhard/signal-cli-rest-api
    
    –-name  		… name for the container
    -d			… detach, run in background, print id → podman ps to list containers, podman attach to reattach
    -t 			… tty, allocate a pseudo-tty and attach to the standard input of the container
    -i			… interactive, keep stdin open even if not attached
    -v			… volume: map host-dir with container-dir; host-dir:container-dir, user permission must be same as podman run user
    --env-file		… line delimited file of environment variables
    
    $ curl -X 'GET' -H 'accept: application/json' 'localhost:9001/v1/about'
        -o <outputfile>
        -v verbose … print also http headers etc.
    
    $ curl -X 'GET' -H 'accept: application/json' -o signalqrlink.png 'localhost:9001/v1/qrcodelink?device_name=BroadcastGreen'
    
    # stop a container
    $ podman stop <containerid>
    # force remove a container (volumes left over after stop)
    $ podman rm -f <containerid> 

Container Volumes

- opt/signal
    - etc   ... config files (ENV)
    - bl    ... volume for the bl 'signal-api' container
    - poc   ... volume for the pioneers of change 'signal-poc' container

autossh
--> https://linuxize.com/post/how-to-setup-ssh-tunneling/

- https://www.harding.motd.ca/autossh/
- https://formulae.brew.sh/formula/autossh
- https://www.harding.motd.ca/autossh/README.txt
