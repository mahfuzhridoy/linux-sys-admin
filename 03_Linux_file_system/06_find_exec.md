# find and exec
The combination of find and -exec is one of the most powerful toolsets for linux administartor. It bridges the gap between locating files and taking immediate , automated action on them, eleminating the need for slow, manual loops in bash scripts.

### Some useful combinations

Common administrative use cases:
- Log and cache maintenance: ```find /var/log -type f -name "*.log" -mtime +30 -exec rm -f {} \;```. This finds all log files older than 30 days and deletes them safely

- Mass permission correction: ```find /var/www/html -type d -exec chmod 755 {} \;```,
```find /var/www/html -type f -exec chmod 644 {} \;```. This Standardizes web directory permission to 755 and files to 644 in one sweep

- Automate backup and Archiving: ```find /home/user/documents -name "*.pdf" -exec cp {} /backup/pdfs/ \;```. This collects all the pdf files scattered across a users directory and copies them to central backup folder

- Security auditing: ```find / -perm -0002 -type f -exec chmod o-w {} \;```. This scans the system for world-writable files and strips the write permission from "others".

## Performance
Understanding how ```-exec``` terminates determines how heavily it impacts system resources:

- ```-exec command {} \;``` Runs the command once for every single file found. This can spawn thousands of processes and slow down the server.

- ```-exec command {} +``` Bundles all the found files together and runs the command only once (similar to xargs). This is significantly faster and uses less cpu.

## Option -ok
The ```-ok``` option in the place of ```-exec``` becomes handy if a potentially dangerous command is run. This will ask if the user wants to execute it or not for every file.

