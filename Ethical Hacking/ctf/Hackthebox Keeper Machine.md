## nmap 

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.9p1 Ubuntu 3ubuntu0.3 (Ubuntu Linux; protocol 2.0)
80/tcp open  http    nginx 1.18.0 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel


## Information Disclosure

»|« RT 4.4.4+dfsg-2ubuntu1 (Debian) Copyright 1996-2019 [Best Practical Solutions, LLC](http://www.bestpractical.com?rt=4.4.4+dfsg-2ubuntu1)
Distributed under [version 2 of the GNU GPL](http://www.gnu.org/licenses/gpl-2.0.html).  
To inquire about support, training, custom development or licensing, please contact [sales@bestpractical.com](mailto:sales@bestpractical.com).

| 27  | lnorgaard  | Lise Nørgaard  | lnorgaard@keeper.htb  | Enabled |
|-----|------------|----------------|-----------------------|---------|
| 14  | root       | Enoch Root     | root@localhost        | Enabled |


# Possible cross-site request forgery

RT has detected a possible **cross-site request forgery** for this request, because the Referrer header supplied by your browser (tickets.keeper.htb:80) is not allowed by RT's configured hostname (keeper.htb:80). A malicious attacker may be trying to **modify a dashboard** on your behalf. If you did not initiate this request, then you should alert your security team.

If you really intended to visit http://keeper.htb/rt/Dashboards/Modify.html , http://keeper.htb/rt/Ticket/Create.html , http://keeper.htb/rt/Ticket/Update.html and modify a dashboard, then **[click here to resume your request](http://keeper.htb/rt/Dashboards/Modify.html?CSRF_Token=b822d443305fd725f154ed24d5e78f58)**.

### [<webmaster@keeper.htb>](http://tickets.keeper.htb/rt/Ticket/Display.html?id=300000#)


## SSH CVE

### CVE-2021-36368

SSh username => lnorgaard 
password =>  Welcome2023!

## DOWNLOADING FILES THROUGH SSH
sudo scp lnorgaard@keeper.htb:KeePassDumpFull.dmp /pwst

## /etc/passwd file can read without root

root:x:0:0:root:/root:/bin/bash

## Try to get the root key by opening pdbx file 
i tried to share the file to the windows with several attempts ,but not worked.
lastly i tried a web virsion of that software 
https://app.keeweb.info/

this worked well