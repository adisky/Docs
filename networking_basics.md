# Networking Basics

https://docs.openstack.org/neutron/queens/admin/intro-basic-networking.html

IP address and classless inter-domain routing (CIDR)
```
192.0.2.5/24          24bits are network
or 
192.0.2.5             24bits are network 
255.255.255.0
```
**Ethernet and ARP**: Machines connected to switch communicate using MAC addresses  
TCP/IP applications addresses with IP+port  
TCP/IP applications->IP+port-> Operating system, checks if it knows mac address of other computer if not  
it sends ARP request in broadcast domain and find MAC associated with IP address. In ARP request it asks who has this IP, please respond with your MAC address??  
```
arping -I eth0 192.0.2.132
```

**ARP cache**: To reduce arping request operating system has an internal cache in which IP address maps to MAC   
```
arp -n
```
**DHCP**: to assign ip address automatically from dhcp server  
dhcp server should be in a same network.  
clients wants IP address send request from port 68 to IP 255.255.255.255 (local broadcast)port 67  
server replies with offering an IP address  
openstack uses dnsmasq  

**IP**: to route packets on different networks  
```
route -n
ip route show
ip route get <ip address>
```
machines on same subnet communicates directly without a router or gateway  
a gateway is a default router, if no other rules matched it forwards to the packet to gateway, dhcp server  
typically transmits a default gateway with IP address  

## Virtual Networking Basics

Physical computer->NIC->port-cable-port->switch  
Virtual Machine->VNIC->port-cable-port->switch  


VLAN : segregation or isolation of traffic on switch, VLAN tagging  

Linux Bridge is a switch, which connects VNIC to pNIC  

VM-> vnet0->linux bridge->eth0  
          Tap interface

## Docker Networking:  

https://mesosphere.com/blog/networking-docker-containers/

Containers are just processes on a host
So containers can use host IP address and run any services  on any host port

But problem is if you want to expose multiple services on port 80 then there will be clashes.

So docker gives option of bridge networking, in which it creates a linux bridge and assign IP address to each container from dhcp server. It gives separate network namespaces to each container. But problem with this approach is when you want to expose your container you map it with a host port and IP that is NAT.

So another option is using a network plugin

* Docker exec(to execute a command in running container)
* Docker run -it (to run container in interactive mode)
* Docker images (List images)
* Docker commit (make a new image from container)

You can expose docker container  service to any port on host
```
docker run -it --name echo-server -p 45678:45678 ubuntu:14.04 bash
```

One docker container can connect to another docker container via two approach
* Connect via host using the exposed port (both containers can expose their ports to host)
* Connect using linked container, in link container docker writes /etc/host file of container with ip addresss of other container. 
  But in approach 2 suppose one is your database service another is web service, and if db server goes down and comes up its IP gets       changes, so this approach has to be tracked manually

Another way is dynamic linking, in dynamic linking a docker network is created, both container will run same network and a name server is used to resolve containers not ip
```
docker network create example
docker run --rm  -ti --link server --net=example --name server ubuntu:14.04 bash
docker run --rm  -ti --link server --net=example --name client ubuntu:14.04 bash
```



