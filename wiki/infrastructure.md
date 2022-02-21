Infrastructure
==============

## Software

### System

- [Kubernetes](https://kubernetes.io/)
    - https://kubernetes.io/docs/home/
    - https://github.com/godaddy/kubernetes-client
    - https://github.com/kubernetes-client/javascript/tree/master/examples
    - ! https://www.redhat.com/sysadmin/compose-kubernetes-podman
- [Podman](https://podman.io/)
    - https://docs.podman.io/en/latest/Commands.html
- [Prometeus](https://prometheus.io/) Appliance Monitoring    
- [Grafana](https://grafana.com/) UI for monitoring
- [Nagios](https://www.nagios.org/) Network Monitoring
- [Nginx](https://www.nginx.com/) HTTP Proxy
    - [Nginx Proxy Manager](https://nginxproxymanager.com/guide/)
        - https://www.nginx.com/products/nginx/live-activity-monitoring/
        - https://github.com/NginxProxyManager/nginx-proxy-manager
        - https://github.com/schenkd/nginx-ui

### DevOps
- [FLUX](https://github.com/fluxcd/flux2) deploy to Kubernetes Clusters
- [Krius](https://github.com/infracloudio/krius) manage Prometheus, Thanos & friends across multiple clusters easily for scale
    - https://www.infracloud.io/blogs/krius-accelerating-monitoring-adoption/
        
Info:
- https://logz.io/blog/prometheus-vs-nagios-metrics/
- https://www.educba.com/prometheus-vs-nagios/
- https://www.metricfire.com/blog/prometheus-vs-nagios/

## V Server

- https://vergleich.focus.de/artikel/die-besten-vserver-im-vergleich_194211
- https://www.hosttest.de/vergleich/vserver.html

### Anbieter

- https://www.netcup.de/vserver/vps.php -> 40,80TB Traffic
- https://www.hosteurope.de/
    - https://www.hosteurope.de/Server/Virtual-Server/  -> Unlimited Traffic?
- https://www.hetzner.com/de/cloud  -> 20TB Traffic
- https://www.hosting.de/
    - https://www.hosting.de/server/ -> 5TB Traffic
- https://www.ionos.de/
    - https://www.ionos.de/server/vps#tarife     -> Unlimited Traffic?
    - https://www.ionos.at/

- https://aws.amazon.com/de/lightsail/

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
