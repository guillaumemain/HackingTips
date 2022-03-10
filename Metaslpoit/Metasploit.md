
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
