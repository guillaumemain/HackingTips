Passive reconnaissance: rely on puclicly available knowledge

*whois*: query WHOIS servers

*nslookup*: query DNS servers

*dig*: query DNS servers


** WHOIS

A WHOIS server listens on port 43 for incoming requests.

*whois*: get regsitrar, DNS, ....

**nslookup and dig

nslookup: find IP address of domain name

    nslookup -type=[A,AAA,MX,...] domain_name server 
  
(type A = IPv4 addresses

type AAA = IPv6 addresses

type MX = Mail server addresses)
    
(1.1.1.1 for cloudflare, 8.8.8.8 for google...)
    
     
