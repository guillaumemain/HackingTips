## Active Reconnaissance

The browser connects to:
* TCP port 80 for HTTP
* TCP port 443 for HTTPS



----------------
### traceroute (tracert on Windows)

    
    traceroute MACHINE_IP
    
traceroute sends successive packets with TTL 1, then 2, then 3, ...

Answer of the form:
    
    1 first_router time_of_reponse first_router_prime time_of_reponse ....
    2 second_router ....



----------------
### telnet

Default port: 23

Sends data in cleartext (use SSH for secure alternative).

Useful to connect to any device and discover its banner

    telnet MACHINE_IP PORT
    
Then input:

    GET /HTTP/1.1    // or SMTP or POP3 if we connect to a mail server
    host: example    // necessary to input some value for the host to avoid getting an error

Answer includes type and version of the install web server


----------------
### netcat

Supports TCP and UDP protocols.
It can function as:
* a client that connects to a listening port
* a server that listens on a port of your choice

Hence, it is a convenient tool to use as a simple client or server over TCP or UDP.

        nc MACHINE_IP PORT       // as client
        nc -lvnp PORT_NUMBER     // as server
        
Options:
* -l: listen mode
* -p: specify port number
* -n: numeric only, no hostname resolution via DNS
* -v: verbose
* -vv: very verbose
* -k: keeps listening after client disconnects

NB. Port numbers less than 1024 require root privileges to listen on.


-------------
### summary

* traceroute: map the path to the target
* ping: check if the target system responds to ICMP echo
* telnet: check which ports are open and reachable by tempting to connect to them
* 
