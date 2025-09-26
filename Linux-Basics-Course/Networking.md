### What I Learned

# DNS

* You can append in IP addresses and custom host names in the /etc/hosts file.
* In larger scale applications where we have more IPs than humanly managble we implement a Domain Name Server
  - Any device that wants to know another IP asks the domain name server and refreences its data not its own.
* /etc/resolv.conf holds the information associated with the DNS server.
  - you can have multiple name servers so if you wanted to connect to something on the internet you can set googes 8.8.8.8 for example to act as a dns for anything on its list.
  - Your DNS can also opt to forward any unknown domain names to another name server so its applied across your entire intranet.
  - You can add a search so internal sites dont need to be searched for with the entire service.domain.root you can add a 'search domain.root' so pings to service resolve as service.domain.root to save time.
* /etc/nsswitch.conf lets us determine whether we resolve ips through dns or through our hosts file assuming we have 2 identical names.
* Record Types on DNSs
  - A - webservers - IPv4
  - AAAA - webservers - Ipv6
  - CNAME - direct links
* nslookup web.add.ress to look up domains on the DNS cant reference /etc/hosts
* dig can be used the same way for more details.

# Networking Basics

* ip link lets us see the interfaces used on any machine physical or virtual.
* we can runn ip addr add 192.168.0.1/24 dev eth0 on device 1.
* we can runn ip addr add 192.168.0.2/24 dev eth0 on device 2.
* This way both devices recognize their interfaces connection to a particular device.
* ip route add ip.on.diff.network/24 via def.ault.gate.way
* WORKS PER DEVICE
* ip route add default via def.ault.gate.way to add a default gateway to a device.
* if we have multi router setups we only need them to help connect to the specific networks they are working for.
  - ie our default gateway can work to serve our internet connections.
  - we can setup other gateways to internal networks but remember its specific to that network and must be configured on the other devices we are trying to connect to aswell.

# Toubleshooting

* Validate the URL.
* Check to make sure local interface is UP
* nslookup to the address to see if its valid and recognized by the DNS
* Now that we know it exist and that our machine can ping we ping the address.
  - If this works you can connect
  - If not:
    - we can run a trace route to the IP address.
    - this will show us the hops we CAN make and where that ends.
    - If this stops at the ruter connected to the other switch we have to start solving from the other end of the connection. If not it may be a networking issue between the router and the next router.
    - If we want to check to see if the HTTP is set to port 80 we can run a:
      - netstat -an | grep 80 | grep -i LISTEN to look to see if port 80 is linked and listening. So the web server can be validated as active.
    - While still on the other machine we check to see if its ports are UP. - iplink
    - Then we check to make sure it can resolve connections through its own default gateway. - ip route add default via gatewayaddress dev interface
    - then you exit your remote connection to the other device and retry the pink or url on the original host.

### What I Did

# Lab 1
  - Searched for the dns server in /etc/resolv.conf
  - used vi to edit the file and change the dns to 8.8.8.8
  - found the search in the dns config to find out what our short hands resolve as.

#Lab 2
  - has you confirm you know how to find the routes and adresses currently known an an interface.
  - ssh to another host you cant resolve an ip on.
  - turn the status of that port to UP
  - then configure the routers port as your default gateway on that remote server.
  - I went back to the original device and now pings to the initially failing server port work.

### Important Notes

The path to reach a website is often backwards from the way we read it ie.
  apps.google.com First your own networks DNS searches and if it cant find it it forwards to a root dns which then find the .com dns as its root. Then .com forwards to .google dns and finally we get access to the IP associated with apps in the .google dns.
  These IPs then are cached by your DNS so it can quickly find access to that domain again.

ip link list and modify interfaces on the host.
ip addr lets us see the ips on those interfaces
  - add allows us to chnage that ipaddress for that interface
ip route shows us the routing tables for out device.
ip route add lets us add certain ip addresses via a gate way we have to define.

Stay procedural when trouble shooting and consider all points of failure.
