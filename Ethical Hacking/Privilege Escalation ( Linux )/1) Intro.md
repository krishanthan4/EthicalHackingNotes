### use these resources as reference

- payloadsAllTheThings


after gained access for the machine 

- [ ] first check for system Information

- hostname
- uname -a
- cat /proc/version
- cat /etc/issue
- lscpu

- [ ] check the processes running

- ps aux

- [ ] secondly check the user infomation

- whoami
- id
- sudo -l  👉 for check which commands we can use in sudo with no passwords.
- cat /etc/group
- cat /etc/passwd
- cat /etc/shadow
- history 
- sudo su -  👉   for change the user as root

- [ ] Network Enumeration

- ifconfig
- ip a
- ip route
- arp -a
- ip neigh
- netstat -ano

- [ ] Password Enumeration 

- ![[Pasted image 20230528115137.png]]  


## Tools

### 1) LinPEAS
**2) LinEnum**
#### 3) linux-exploit-suggester
##### 4) Linuxprivchecker


bash linpeas.sh
linux-exploit-suggester 👉  for vulnerabilities on the machine


