## Passive reconnaissance: rely on puclicly available knowledge

*whois*: query WHOIS servers

*nslookup*: query DNS servers

*dig*: query DNS servers

-----------
### WHOIS

A WHOIS server listens on port 43 for incoming requests.

    whois domain

*whois*: get regsitrar, DNS, ....



-----------
### nslookup and dig

nslookup: find IP address of domain name

    nslookup -type=[A,AAA,MX,...] domain_name server 
  
* type A = IPv4 addresses
* type AAA = IPv6 addresses
* type MX = Mail server addresses
* type CNAME = canonical name
* type SOA = start of authority
* type TXT = TXT records


* server = 1.1.1.1 for cloudflare, 8.8.8.8 for google...
    
 
*dig* is more advanced and has more functionality

    dig @server domain type
     
 ----------
 ### Find subdomains and other info
 
[DNSDumpster](https://dnsdumpster.com/)
 
[Shodan.io](https://www.shodan.io/)

