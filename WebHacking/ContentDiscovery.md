## Manual discovery

* robots.txt: document that tells search engines which pages they are and aren't allowaed to show on their search engine results

* favicon (small icon displayed in browser's address bar): can give a clue of the framework being used. md5 hash value of some favicons: https://wiki.owasp.org/index.php/OWASP_favicon_database

* sitemap.xml: list of every file the website owner wishes to be listed on a search engine

* HTTP headers: can contain info about webserver software, programming/scripting language in use

* OSINT (open-source intelligence) with Google Hacking/Dorking (https://en.wikipedia.org/wiki/Google_hacking):
  * site:example.com
  * inurl:term
  * filetype:pdf
  * intitle:term
  
* [Wappalyzer](https://www.wappalyzer.com/)

* [wayback machine](https://archive.org/web/): historical archive of websites that date back to the late 90s

* http(s)://{name}.s3.amazonaws.com. S3 buckets allows people to save files and static website content accessible over HTTP(S). The owner can set access permissions.
Can be {name}-assets, {name}-www, {name}-public, {name}-private, etc.





------------------


## Subdomain discovery

### Search engines
    
    -site:www.example.com
    -site:*.example.com
    

### SSL/TLS certificates

SSL (Secure Sockets layer) / TLS (Transport Layer Security) certificates are created for a domain by a CA (Certificate Authority). CAs take part in "CT logs" (Certificatio Transparency), which are made publibly available. Can be used to discover subdomains:
- https://crt.sh
- https://transparencyreport.google.com/https/certificates

### wordlists
https://github.com/danielmiessler/SecLists

### Sublist3r
Automate the subdomain discovery

    sublist3r -d kali.org -t 3 -e bing    // Search for subdomains of kali.org (-d kali.org) using the Bing search engine (-e bing) with 3 threads (-t 3)
    


### gobuster and dirb

brute-forcing web directories
    
    gobuster -u example.com -w wordlist.txt
