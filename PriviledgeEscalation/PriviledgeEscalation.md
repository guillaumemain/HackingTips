## Enumeration

system OS, version

    hostname    // easily changeable, but ex: SQL-PROD-01 -> production SQL server
    
    uname -a    // kernel used by the system
    
    /proc/version    // target system processes, kernel version, whehter a compiler is installed...
    
    /etc/issue       // about the OS (but can be customized)
    
Processes variables, commands

    ps -A         // all running processes
    ps axjf       // view process tree
    ps aux        // all users (a), user that launched the process (u), processes not attached to a terminal (x)
    
    
    env           // environmental variables
    
    sudo -l       // commands that your user can run using sudo
    
    id [USER]     // user's priviledge level and group memberships
    
    /etc/passwd   // all users (including system or service users) -> grep home from this list for real users
    
netstat

    -a    // show all listening ports and established connections 
    -at   // list TCP protocols
    -au   // list UDP protocols
    -l    // list ports in listening mode
    -s    // network usage statistics (-t and -u to limit to one protocol)
    -tp   // list connections with service name and PID information (PID info will only by displayed in sudo mode if the process is owned by another user)
    -i    // interface stats
    
    -ano  // all sockets; resolve names; display timers

find

    find . -name flag1.txt
    find /home -name flag1.txt
    find / -type d -name config
    find / -type f -perm 0777
    find / -perm a=x               // executable files
    find /home -user frank
    find / -mtime 10               // modified in the last 10 days
    find / -atime 10               // accessed in the last 10 days
    find / -cmin -60               // changed within the last hour
    find / -amin -60               // accessed within the last hour
    find / -size 50M               // files with a 50MB size (+50M size >=50M, -50M ...)
    
NB. find generates errors. We can redirect them to /dev/null
    
    find / -writable -type d 2>/dev/null   // find world-writeable folders
    find / -perm -222 -type d 2>/dev/null  // find world-writeable folders
    find / -perm -o w -type d 2>/dev/null  // find world-writeable folders
    
    find / -perm -u=s -type f 2>/dev/null  // Find files with the SUID bit, which allows us to run the file with a higher privilege level than the current user. 
    

-------------------
## Automated Enumeration Tools

[LinPeas](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS)

[LinEnum](https://github.com/rebootuser/LinEnum)

[LES (Linux Exploit Suggester)](https://github.com/mzet-/linux-exploit-suggester)

[Linux Smart Enumeration](https://github.com/diego-treitos/linux-smart-enumeration)

[Linux Priv Checker](https://github.com/linted/linuxprivchecker)
