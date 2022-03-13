[ffuf](https://github.com/ffuf/ffuf): fast web fuzzer written in Go
(good tutorial: https://codingo.io/tools/ffuf/bounty/2020/09/17/everything-you-need-to-know-about-ffuf.html)


### Subdomain discovery

    ffuf -w wordlist.txt -u fuzzed_url.com -c // -c for color, -v for verbose 

    -w              // wordlist path
    
    -x GET/POST     // request method
    
    -d              // data we are sending, with FUZZ being the keyword being replaced by the words in the file -w
    
    -H              // adds additional headers
    
    -u              // url
    
    -mr             // text response we are looking for
    

Example:

    ffuf -w wordlist.txt
      -X POST -d "username=FUZZ"
      -H "Content-Type: application/x-www-form-urlencoded"
      -u http://10.101.23.12
      -mr "username already exists"
    
    
    ffuf -w w1:wordlist1.txt, w2:wordlist2.txt
       -X POST -d “username=W1&password=W2”
       -H “Content-Type: application/x-www-form-urlencoded”
       -u http://10.10.114.80/customers/login
       -fc 200   // checks for HTTP status codes other than 200 ("Everything is OK")
      
 
 
 
filter flags:

  -fc     // filter on content length
  -fl     // filter on number of lines in response
  -fw     // filter words 

  -d      // specifies the data we are send, with F
