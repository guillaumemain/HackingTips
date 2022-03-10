
### msfconsole modules

can be found under /opt/metasploit-framework/modules

* auxiliaries: scanners, crawlers, fuzzers
* encoders (not considered as evaders)
* evaders (evade antivirus software)
* exploits
* NOPs (No OPeration) (do nothing, represented in the Intel x86 CPU family with 0x90, following which the CPU will do nothing for one cycle; used as a buffer to achieve consistent payload sizes)
* payloads (codes that will run on the target system)
  * singles: self-contained payloads
  * stagers: reponsible for setting up a connection between Metasploit and the target system to download the stages
  * stages: downloaded by the stager

NB. To differentiate singles(=inlines) from staged exploits:
* generic/shell_reverse_tcp is a single
* windows/x64/shell/reverse_tcp is a staged payload


-------------
### msfconsole

    use module_path
    show payloads
    back
    info
    search [type:module_type] module_name   // module_type = auxiliary ....
    use search_result_number
    show options
    set PARAMETER_NAME VALUE


### common parameters

* RHOSTS: remote host (single IP or network range)
* RPORT: remote port
* PAYLOAD: localhost (attacking machine IP address)
* LPORT: local port you will use for the reverse shell to connect back to
* SESSION: each connection established to the target system using Metasploit will have a session ID. You will use this with post-exploitation modules that will connect to the target system using an existing connection.

    unset PARAMETER_NAME   // clear one parameter value
    unset all   // clear everything
    setg PARAMETER_NAME VALUE   // globally set
    unsetg PARAMETER_NAME
    
    exploit    // "run" also works
        -z     // background the session as soon as it opens
        
    background   // or CTRL+Z to background the session
    sessions     // list of existing sessions
    
    session -i SESSION_ID    // get back to the session
    






