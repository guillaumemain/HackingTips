## SSL/TLS certificates

SSL (Secure Sockets layer) / TLS (Transport Layer Security) certificates are created for a domain by a CA (Certificate Authority). CAs take part in "CT logs" (Certificatio Transparency), which are made publibly available. Can be used to discover subdomains:
- https://crt.sh
- https://transparencyreport.google.com/https/certificates

----------
## Search engines
    
    -site:www.example.com
    -site:*.example.com

----------
## Sublist3r
Automate the subdomain discovery

    sublist3r -d kali.org -t 3 -e bing    // Search for subdomains of kali.org (-d kali.org) using the Bing search engine (-e bing) with 3 threads (-t 3)
    
    
----------
## ffuf (good tutorial: https://codingo.io/tools/ffuf/bounty/2020/09/17/everything-you-need-to-know-about-ffuf.html)
Subdomain discovery from wordlist

    ffuf -w wordlist.txt -u fuzzed_url.com -c // -c for color, -v for verbose 
    
wher fuzzed_url can be:
    
    test.com?id=FUZZ
    
    test.com?FUZZ=32
    
can add a POST flag:

    ffuf -w wordlist.txt -u tests.com -X POST -d "username=admin\&password=FUZZ"

filter flags:
  -fc     // filter on content length
  -fl     // filter on number of lines in response
  -fw     // filter words 
