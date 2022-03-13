## IDOR

Insecure Direct Object Reference: it is a type of access control vulnerability.

Common type of encoding used by websites: base64

Find IDOR in Hashes: https://crackstation.net/

If the user ID cannot be detected using the above methods, create two accounts and swap the IDs.

------------------
## Path traversal
Common files useful to access on linux machine:
- /etc/issue: contains a message or system identification to be printed before the login prompt
- /etc/profile: controls system-wide default variables
- /proc/version: version of Linux kernel
- /etc/passwd: all registered users that have access to the system
- /etc/shadow: info about the users' passwords
- /root/.bash_history
- /var/log/dmesg or dmessage: contains global system messages (including thoses that are logged during startup)
- /var/mail/root: all emails for root user
- /root/.ssh/id_rsa: private SSH keys for a root or any known valide user on the server
- /var/log/apache2/access.log: accessed resquests for Apache webserver

On windows:
- C:\boot.ini: contains the boot options for computers with BIOS firmware

The functions that causes path traversal vulnerabilities in PHP is: file_get_contents

--------------------
## Local File Inclusion (LFI)
