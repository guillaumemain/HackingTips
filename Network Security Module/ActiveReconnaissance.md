## Active Reconnaissance

The browser connects to:
* TCP port 80 for HTTP
* TCP port 443 for HTTPS



----------------
### traceroute
    
    traceroute MACHINE_IP
    
traceroute sends successive packets with TTL 1, then 2, then 3, ...

Answer of the form:
    
    1 first_router time_of_reponse first_router_prime time_of_reponse ....
    2 second_router ....



----------------
### telnet

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

