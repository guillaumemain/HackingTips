## Which systems are up

### Enumerate targets

    nmap -options TARGETS
    nmap -iL file.txt
    namp -sL TARGETS (check the hosts that will be scanned without scanning them; ! nmap will attempt a reverse-DNS resolution on all the targets to obtain their name)
    namp -sl -n TARGETS (no reverse-DNS resolution)
    
* TARGETS = list (10.10.23.12 tryackme.com  example.org)  OR  range (10.11.12.14-21)  OR   subnet (MACHINE_IP/24)

--------------------
### nmap host discovery

What nmap does for a:
* privileged user on local subnet: ARP requests
* priviledged user outside the local network: ICMP echo requests, TCP ACK to port 80, TCP SYN to port 443, ICMP timestamp request
* unpriviledged user outside the local network: TCP 3-way handshake by sending SYN pckets to port 80 and 443

By default, nmap uses a ping scan to find live hosts, then poceeds to scan live hosts only.
To avoid port-scanning:
     
     nmap -sn TARGETS

----------------
### on local subnet (ARP)

To perform only ARP requests:
 
    nmap -PR TARGETS

Other tool for ARP scans only:
    
    arp-scan --localnet
    arp-scan -I eth0 -l    // -I: interface (when you are connect to more than one)
    
-------------------
### using ICMP

Ping every IP address (ICMP type 8/ECHO) and wait for ping reply (ICMP Type 0)

NB. Not always reliable: many firewalls block ICMP echo (ex: new version of Windows default firewall)

    nmap -PE TARGETS
    
Send Timestamp request (ICMP Type 13) and wait for Timestamp reply (ICMP Type 14)

    nmap -PP TARGETS
    
Send address mask query (ICMP Type 17) and wait for address mask reply (ICMP Type 18)

    nnap -PM TARGETS
    
------------------------
### using TCP and UDP

TCP SYN ping
    
    nmap -PS[port_number_list] TARGETS  // ex: -PS443 (-PS=80 by default)
    
Unpriviledged user: send SYN, receive SYN/ACK or RST, send ACk
Priviledged user: send SYN, receive SYN/ACK or RST, send RST

NB. -sn option (no port-scanning) is still available


TCP ACK ping (priviledged user only)

    nmap -PS
    
UDP ping

    nmap -PU TARGETS

Port open = no response

Port closed = ICMP destination unreachable (Type 3, Code 3)

NB. Other tool: masscan

    masscan TARGETS -p[port_list_number]/--top-ports number_of_ports  // more aggressive with the rate of packets it generates
    
    
----------------
### using Reverse-DNS lookup

By default, nmap reverse-DNS online hosts:
* -n to skip this step
* -R to query the DNS server even for offline hosts
* --dns-servers DNS_SERVER to specify a specific DNS server




