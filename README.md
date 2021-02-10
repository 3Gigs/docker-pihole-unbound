# Docker-compose file for Pi-Hole & Unbound  

### Runs both Pi-Hole and Unbound and allow them to communicate together
There are many repos that already do this but:
* This **doesn't** use any host network black magic hacks, and allows Pi-Hole to forward to Unbound using **Docker's bridged networks**
* Just pulls already made Docker images, very simple to setup
* Actually works (for me)

Note that the Docker-compose file mounts to **~/.pi and ~/.unbound**. Change this if you don't want files on your home folder

## Instructions
Before you get started check to see if your firewall rules block ports **53, 67/udp, 80/tcp, 443/tcp, 5053/udp**
1. Get [Docker](https://docs.docker.com/engine/install/) **(Raspbian users MUST download via convenience script)** and [Docker-composer](https://docs.docker.com/compose/install/)
2. Clone this repository ```git clone https://github.com/3Gigs/docker-pihole-unbound/```
3. Make any necessary modifications to docker-compose.yml (You may want to change Pi-Hole environment variables **TZ:**, **WEBPASSWORD:**)
4. Run ```docker-compose up --detach```  

If it doesn't work check Unbound's container's network IP. I don't know what affects the order of the IPs. If it still doesn't work run ```docker logs <CONTAINER_NAME>``` to see what's wrong
