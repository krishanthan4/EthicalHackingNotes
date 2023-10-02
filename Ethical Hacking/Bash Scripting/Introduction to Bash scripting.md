## Bourne Again Shell

- Bash is a scripting language used to communicate with Unix-based OS and give commands to the system.
- Windows Subsystem for Linux, introduced in May 2019, allows using Bash in a Windows environment.
- Mastering Bash is essential for efficient work.
- Scripting languages, like Bash, do not require code compilation for execution.
- Penetration testers need to work with different operating systems, including Windows and Unix-based.
- Efficiency in privilege escalation depends on system knowledge, terminal usage, data filtering, and process automation.
- Large Unix-based enterprise networks require sorting and filtering large amounts of data for quick identification of gaps and information.
- Scripting combines commands and improves speed and efficiency.
- Scripting languages share a structure with programming languages, including input/output, variables, conditional execution, loops, etc.
- Automation of processes and handling large data volumes is common in scripting.
- Scripts are executed by an interpreter, such as Bash, without creating separate processes.
- Script execution involves specifying the interpreter and the script to be processed (e.g., `bash script.sh <optional arguments>`).

Like a programming language, a scripting language has almost the same structure, which can be divided into:

- Input & Output
- Arguments, Variables & Arrays
- Conditional execution
- Arithmetic
- Loops
- Comparison operators
- Functions

# Working Components

## Conditional Execution

It allows us to control the flow of a script, by reaching different **conditions**. It is like **if** statements in Python. 

```bash
#!/bin/bash

# Check for given argument
if [ $# -eq 0 ]
then
	echo -e "You need to specify the target domain.\n"
	echo -e "Usage:"
	echo -e "\t$0 <domain>"
	exit 1
else
	domain=$1
fi

<SNIP>
```

- `#!/bin/bash` - Shebang.
- `if-else-fi` - Conditional execution.
- `echo` - Prints specific output.
- `$#` / `$0` / `$1` - Special variables.
- `domain` - Variables.
- `-eq` - Comparison Operator



### Shebang

- Top of the script

- Starts with `#!`

- Contains path to the specified interperter (/bin/bash)



Use different interperters like **Python and Perl**. 

```bash
#!/usr/bin/env python
```

```bash
#!/usr/bin/env perl
```

### If-Else-Fi

- Different conditions
  
  - If-else conditions
  
  - Case statements

### If-Only.sh

```bash
#!/bin/bash

value=$1

if [ $value -gt "10" ]
then
        echo "Given argument is greater than 10."
fi
```

#### If-Only.sh - Execution

```shell-session
DanielBoye@htb[/htb]$ bash if-only.sh 5
```

```shell-session
DanielBoye@htb[/htb]$ bash if-only.sh 12

Given argument is greater than 10.
```

### If-Elif-Else.sh

```bash
#!/bin/bash

value=$1

if [ $value -gt "10" ]
then
    echo "Given argument is greater than 10."
elif [ $value -lt "10" ]
then
    echo "Given argument is less than 10."
else
    echo "Given argument is not a number."
fi
```

#### If-Elif-Else.sh - Execution

  If-Elif-Else.sh - Execution

```shell-session
DanielBoye@htb[/htb]$ bash if-elif-else.sh 5

Given argument is less than 10.
```

### Several Conditions - Script.sh

Example of different conditions in bash.

```bash
#!/bin/bash

# Check for given argument
if [ $# -eq 0 ]
then
    echo -e "You need to specify the target domain.\n"
    echo -e "Usage:"
    echo -e "\t$0 <domain>"
    exit 1
elif [ $# -eq 1 ]
then
    domain=$1
else
    echo -e "Too many arguments given."
    exit 1
fi

<SNIP>
```

### Exercise Script

```bash
#!/bin/bash
# Count number of characters in a variable:
#     echo $variable | wc -c

# Variable to encode
var="nef892na9s1p9asn2aJs71nIsm"

for counter in {1..40}
do
        var=$(echo $var | base64)
done
```

### Q: Create an "If-Else" condition in the "For"-Loop of the "Exercise Script" that prints you the number of characters of the 35th generated value of the variable "var". Submit the number as the answer.

I need to make a if-else condition inside of the for-loop. I will use the provided code for counting the number of characters in a variable `echo $variable | wc`.



This is my solution for the if-else condition

```bash
if [ $counter -eq 35 ]; then
    character_count=$(echo $var | wc -c)
    echo $character_coun
```



Final script 

```bash
#!/bin/bash
# Count number of characters in a variable:
#     echo $variable | wc -c

# Variable to encode
var="nef892na9s1p9asn2aJs71nIsm"

for counter in {1..40}
do
        var=$(echo $var | base64)
		if [ $counter -eq 35 ]; then
            character_count=$(echo $var | wc -c)
            echo $character_count
        fi
done
```









## Arguments, Variables, and Arrays

Pass up to **9** argument

- Special variables

- Placeholders

### CIDR.sh

```bash
#!/bin/bash

# Check for given argument
if [ $# -eq 0 ]
then
    echo -e "You need to specify the target domain.\n"
    echo -e "Usage:"
    echo -e "\t$0 <domain>"
    exit 1
else
    domain=$1
fi

<SNIP>
```

### Special Variables

- Internal Field Seperator (**IFS**)

| **IFS** | **Description**                                                                                                                                                         |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `$#`    | This variable holds the number of arguments passed to the script.                                                                                                       |
| `$@`    | This variable can be used to retrieve the list of command-line arguments.                                                                                               |
| `$n`    | Each command-line argument can be selectively retrieved using its position. For example, the first argument is found at `$1`.                                           |
| `$$`    | The process ID of the currently executing process.                                                                                                                      |
| `$?`    | The exit status of the script. This variable is useful to determine a command's success. The value 0 represents successful execution, while 1 is a result of a failure. |

### Variables

No space between names and values

Dollar sign intended to allow this variable value to be used in **other code sections**

- Like a global variable

```bash
domain=$1
```

- No differentiation in recognition of variables like
  
  - Strings
  
  - Integers
  
  - Boolean

- All content treated as **string characters**

### Arrays

- Assigning several values
  
  - Scan multiple domains or IP adresses

- Index starts at **0**

#### Arrays.sh

This will print out the first adress

```bash
#!/bin/bash

domains=(www.inlanefreight.com ftp.inlanefreight.com vpn.inlanefreight.com www2.inlanefreight.com)

echo ${domains[0]}
```

---

This will print them all since they are in a `" "`

```bash
#!/bin/bash

domains=("www.inlanefreight.com ftp.inlanefreight.com vpn.inlanefreight.com" www2.inlanefreight.com)
echo ${domains[0]}
```

### Q: Submit the echo statement that would print "www2.inlanefreight.com" when running the last "Arrays.sh" script.

Here is the script

```bash
#!/bin/bash

domains=("[www.inlanefreight.com](http://www.inlanefreight.com) ftp.inlanefreight.com vpn.inlanefreight.com" www2.inlanefreight.com)
echo ${domains[0]}
```

The first thing that I see is that the three adresses is in a quotation mark, so to print out the last adress we need to access the index `[1]`. 



To do this we edit the echo command to this `echo ${domains[1]}`


## Comparison Operators

- String operators

- Integer operators

- File operators

- Boolean operators

### String operators

| **Operator** | **Description**                             |
| ------------ | ------------------------------------------- |
| `==`         | is equal to                                 |
| `!=`         | is not equal to                             |
| `<`          | is less than in ASCII alphabetical order    |
| `>`          | is greater than in ASCII alphabetical order |
| `-z`         | if the string is empty (null)               |
| `-n`         | if the string is not null                   |

- Note: when the variable is `$1`, we need to put it in double-quotes. 
  
  - This is becasue the content should be handled as a **string**

```bash
#!/bin/bash

# Check the given argument
if [ "$1" != "HackTheBox" ]
then
    echo -e "You need to give 'HackTheBox' as argument."
    exit 1

elif [ $# -gt 1 ]
then
    echo -e "Too many arguments given."
    exit 1

else
    domain=$1
    echo -e "Success!"
fi
```

- Comparisons only work within the **double square brackets** `[[ <condition> ]]`

ASCII table

```shell-session
DanielBoye@htb[/htb]$ man ascii
```

### ASCII Table

| **Decimal** | **Hexadecial** | **Character** | **Description** |
| ----------- | -------------- | ------------- | --------------- |
| 0           | 00             | NUL           | End of a string |
| ...         | ...            | ...           | ...             |
| 65          | 41             | A             | Capital A       |
| 66          | 42             | B             | Capital B       |
| 67          | 43             | C             | Capital C       |
| 68          | 44             | D             | Capital D       |
| ...         | ...            | ...           | ...             |
| 127         | 7F             | DEL           | Delete          |

### Integer Operators

- Comparing integers

| **Operator** | **Description**             |
| ------------ | --------------------------- |
| `-eq`        | is equal to                 |
| `-ne`        | is not equal to             |
| `-lt`        | is less than                |
| `-le`        | is less than or equal to    |
| `-gt`        | is greater than             |
| `-ge`        | is greater than or equal to |

```bash
#!/bin/bash

# Check the given argument
if [ $# -lt 1 ]
then
    echo -e "Number of given arguments is less than 1"
    exit 1

elif [ $# -gt 1 ]
then
    echo -e "Number of given arguments is greater than 1"
    exit 1

else
    domain=$1
    echo -e "Number of given arguments equals 1"
fi
```

### File Operators

- Find out **specific premissions** or **if they exist**

| **Operator** | **Description**                                        |
| ------------ | ------------------------------------------------------ |
| `-e`         | if the file exist                                      |
| `-f`         | tests if it is a file                                  |
| `-d`         | tests if it is a directory                             |
| `-L`         | tests if it is if a symbolic link                      |
| `-N`         | checks if the file was modified after it was last read |
| `-O`         | if the current user owns the file                      |
| `-G`         | if the file’s group id matches the current user’s      |
| `-s`         | tests if the file has a size greater than 0            |
| `-r`         | tests if the file has read permission                  |
| `-w`         | tests if the file has write permission                 |
| `-x`         | tests if the file has execute permission               |

```bash
#!/bin/bash

# Check if the specified file exists
if [ -e "$1" ]
then
    echo -e "The file exists."
    exit 0

else
    echo -e "The file does not exist."
    exit 2
fi
```

### Boolean and Logical Operators

- True or false

- We can use string operators
  - If they match, we get a boolean value

```bash
#!/bin/bash

# Check the boolean value
if [[ -z $1 ]]
then
    echo -e "Boolean value: True (is null)"
    exit 1

elif [[ $# > 1 ]]
then
    echo -e "Boolean value: True (is greater than)"
    exit 1

else
    domain=$1
    echo -e "Boolean value: False (is equal to)"
fi
```

### Logical Operators

- Define several conditions within one
  
  - All conditions must match before the code can be executed

| **Operator** | **Description**        |
| ------------ | ---------------------- |
| `!`          | logical negotation NOT |
| `&&`         | logical AND            |
| `\|`         | logical OR             |

```bash
#!/bin/bash

# Check if the specified file exists and if we have read permissions
if [[ -e "$1" && -r "$1" ]]
then
    echo -e "We can read the file that has been specified."
    exit 0

elif [[ ! -e "$1" ]]
then
    echo -e "The specified file does not exist."
    exit 2

elif [[ -e "$1" && ! -r "$1" ]]
then
    echo -e "We don't have read permission for this file."
    exit 1

else
    echo -e "Error occured."
    exit 5
fi
```

### Exercise Script

```bash
#!/bin/bash

var="8dm7KsjU28B7v621Jls"
value="ERmFRMVZ0U2paTlJYTkxDZz09Cg"

for i in {1..40}
do
        var=$(echo $var | base64)

done
```

### Q: Create an "If-Else" condition in the "For"-Loop that checks if the variable named "var" contains the contents of the variable named "value". Additionally, the variable "var" must contain more than 113,450 characters. If these conditions are met, the script must then print the last 20 characters of the variable "var". Submit these last 20 characters as the answer.

When I tackled this problem my first idea was to have this `If` loop

```bash
if [[ $var == *$value* ]] && [ ${#var} -ge 113469 ] ;
    then
        <...>
    fi
```

And for the printing of the 20 last characters with this

```bash
echo ${var: -20}
```

But it turned out this was the wrong way, since `-20` gives me the wrong answer

To find the last 20 characters you needed to use `-19` to  get the output



Solvescript

```bash
#!/bin/bash

var="8dm7KsjU28B7v621Jls"
value="ERmFRMVZ0U2paTlJYTkxDZz09Cg"

for i in {1..40}
do
    var=$(echo "$var" | base64)

    if [[ $var == *$value* ]] && [ ${#var} -ge 113469 ] ;
    then
        echo ${var: -19}
        break
    fi
done
```

## Arithmetic

- We have **7** different arithmetic operators

- Perform different operations or to modify integers

### Arithmetic Operators

| **Operator** | **Description**                         |
| ------------ | --------------------------------------- |
| `+`          | Addition                                |
| `-`          | Substraction                            |
| `*`          | Multiplication                          |
| `/`          | Division                                |
| `%`          | Modulus                                 |
| `variable++` | Increase the value of the variable by 1 |
| `variable--` | Decrease the value of the variable by 1 |

```bash
#!/bin/bash

increase=1
decrease=1

echo "Addition: 10 + 10 = $((10 + 10))"
echo "Substraction: 10 - 10 = $((10 - 10))"
echo "Multiplication: 10 * 10 = $((10 * 10))"
echo "Division: 10 / 10 = $((10 / 10))"
echo "Modulus: 10 % 4 = $((10 % 4))"

((increase++))
echo "Increase Variable: $increase"

((decrease--))
echo "Decrease Variable: $decrease"
```

Calculate the length of a variable with `${#variable}`. Example is down below

### VarLength.sh

```bash
#!/bin/bash

htb="HackTheBox"

echo ${#htb}
```

Output:

```shell-session
DanielBoye@htb[/htb]$ ./VarLength.sh

10
```

### CIDR.sh

```bash
<SNIP>
    echo -e "\nPinging host(s):"
    for host in $cidr_ips
    do
        stat=1
        while [ $stat -eq 1 ]
        do
            ping -c 2 $host > /dev/null 2>&1
            if [ $? -eq 0 ]
            then
                echo "$host is up."
                ((stat--))
                ((hosts_up++))
                ((hosts_total++))
            else
                echo "$host is down."
                ((stat--))
                ((hosts_total++))
            fi
        done
    done
<SNIP>
```

# Script Control

## Input and Output Control

### Input Control

Controling the input based upon what we want to run next after a manual check

### Output Control

- Output redirections

- Tee utility
  
  - Transfer output and use the pipe (`|`) to forward it to tee
  
  - `-a` / `--append` 
    
    - Ensures that the file is not overwritten
    
    - Supplemented with new results

### CIDR.sh

```bash
<SNIP>

# Identify Network range for the specified IP address(es)
function network_range {
    for ip in $ipaddr
    do
        netrange=$(whois $ip | grep "NetRange\|CIDR" | tee -a CIDR.txt)
        cidr=$(whois $ip | grep "CIDR" | awk '{print $2}')
        cidr_ips=$(prips $cidr)
        echo -e "\nNetRange for $ip:"
        echo -e "$netrange"
    done
}

<SNIP>

# Identify IP address of the specified domain
hosts=$(host $domain | grep "has address" | cut -d" " -f4 | tee discovered_hosts.txt)


```shell-session
DanielBoye@htb[/htb]$ cat discovered_hosts.txt CIDR.txt

165.22.119.202
NetRange:       165.22.0.0 - 165.22.255.255
CIDR:           165.22.0.0/16
```

## Flow Control - Loops

- Branches:
  
  - `If-Else` Conditions
  - `Case` Statements

- Loops:
  
  - `For` Loops
  - `While` Loops
  - `Until` Loops



### For Loops

#### Examples

```bash
for variable in 1 2 3 4
do
    echo $variable
done
```

```bash
for variable in file1 file2 file3
do
    echo $variable
done
```

```bash
for ip in "10.10.10.170 10.10.10.174 10.10.10.175"
do
    ping -c 1 $ip
done
```



Can also write it in a single line



```shell-session
DanielBoye@htb[/htb]$ for ip in 10.10.10.170 10.10.10.174;do ping -c 1 $ip;done

PING 10.10.10.170 (10.10.10.170): 56 data bytes64 bytes from 10.10.10.170: icmp_seq=0 ttl=63 time=42.106 ms--- 10.10.10.170 ping statistics ---1 packets transmitted, 1 packets received, 0.0% packet lossround-trip min/avg/max/stddev = 42.106/42.106/42.106/0.000 msPING 10.10.10.174 (10.10.10.174): 56 data bytes64 bytes from 10.10.10.174: icmp_seq=0 ttl=63 time=45.700 ms--- 10.10.10.174 ping statistics ---1 packets transmitted, 1 packets received, 0.0% packet lossround-trip min/avg/max/stddev = 45.700/45.700/45.700/0.000 ms
```



Now edit the CIDR.sh script



### CIDR.sh

Now we are running through the array `ipadrr`. Output is stored in the `CIDR.txt` file.

```bash
<SNIP>

# Identify Network range for the specified IP address(es)
function network_range {
    for ip in $ipaddr
    do
        netrange=$(whois $ip | grep "NetRange\|CIDR" | tee -a CIDR.txt)
        cidr=$(whois $ip | grep "CIDR" | awk '{print $2}')
        cidr_ips=$(prips $cidr)
        echo -e "\nNetRange for $ip:"
        echo -e "$netrange"
    done
}

<SNIP>
```

### While Loops

- A statement is executed as long as a condition is fulfilled (`true`)

#### CIDR.sh

```bash
<SNIP>
        stat=1
        while [ $stat -eq 1 ]
        do
            ping -c 2 $host > /dev/null 2>&1
            if [ $? -eq 0 ]
            then
                echo "$host is up."
                ((stat--))
                ((hosts_up++))
                ((hosts_total++))
            else
                echo "$host is down."
                ((stat--))
                ((hosts_total++))
            fi
        done
<SNIP>
```

#### WhileBreaker.sh

```bash
#!/bin/bash

counter=0

while [ $counter -lt 10 ]
do
  # Increase $counter by 1
  ((counter++))
  echo "Counter: $counter"

  if [ $counter == 2 ]
  then
    continue
  elif [ $counter == 4 ]
  then
    break
  fi
done
```

```shell-session
DanielBoye@htb[/htb]$ ./WhileBreaker.sh

Counter: 1
Counter: 2
Counter: 3
Counter: 4
```

### Until Loops

- The code inside a `until` loop is executed as long as the particular condition is `false`.

#### Until.sh

```bash
#!/bin/bash

counter=0

until [ $counter -eq 10 ]
do
  # Increase $counter by 1
  ((counter++))
  echo "Counter: $counter"
done
```

```shell-session
DanielBoye@htb[/htb]$ ./Until.sh

Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
Counter: 6
Counter: 7
Counter: 8
Counter: 9
Counter: 10
```

### Exercise Script

```bash
#!/bin/bash

# Decrypt function
function decrypt {
    MzSaas7k=$(echo $hash | sed 's/988sn1/83unasa/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/4d298d/9999/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/3i8dqos82/873h4d/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/4n9Ls/20X/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/912oijs01/i7gg/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/k32jx0aa/n391s/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/nI72n/YzF1/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/82ns71n/2d49/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/JGcms1a/zIm12/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/MS9/4SIs/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/Ymxj00Ims/Uso18/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/sSi8Lm/Mit/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/9su2n/43n92ka/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/ggf3iunds/dn3i8/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/uBz/TT0K/g')

    flag=$(echo $MzSaas7k | base64 -d | openssl enc -aes-128-cbc -a -d -salt -pass pass:$salt)
}

# Variables
var="9M"
salt=""
hash="VTJGc2RHVmtYMTl2ZnYyNTdUeERVRnBtQWVGNmFWWVUySG1wTXNmRi9rQT0K"

# Base64 Encoding Example:
#        $ echo "Some Text" | base64

# <- For-Loop here

# Check if $salt is empty
if [[ ! -z "$salt" ]]
then
    decrypt
    echo $flag
else
    exit 1
fi
```

### Q:  Create a "For" loop that encodes the variable "var" 28 times in "base64". The number of characters in the 28th hash is the value that must be assigned to the "salt" variable.



To make the For Loop I created it with making it itterate through 28 times. And when I ran the original script the `salt=""` created some weird things in my solution, and other peole have encountered the same problem, so I just deleted it. 



Here is the solvescripts:

```bash
#!/bin/bash

# Decrypt function
function decrypt {
    MzSaas7k=$(echo $hash | sed 's/988sn1/83unasa/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/4d298d/9999/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/3i8dqos82/873h4d/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/4n9Ls/20X/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/912oijs01/i7gg/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/k32jx0aa/n391s/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/nI72n/YzF1/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/82ns71n/2d49/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/JGcms1a/zIm12/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/MS9/4SIs/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/Ymxj00Ims/Uso18/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/sSi8Lm/Mit/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/9su2n/43n92ka/g')
    Mzns7293sk=$(echo $MzSaas7k | sed 's/ggf3iunds/dn3i8/g')
    MzSaas7k=$(echo $Mzns7293sk | sed 's/uBz/TT0K/g')

    flag=$(echo $MzSaas7k | base64 -d | openssl enc -aes-128-cbc -a -d -salt -pass pass:$salt)
}

# Variables
var="9M"
hash="VTJGc2RHVmtYMTl2ZnYyNTdUeERVRnBtQWVGNmFWWVUySG1wTXNmRi9rQT0K"

for ((i = 0 ; i < 28 ; i++)); do
echo “Try number $i”
var=$(echo $var | base64)
echo $var | wc -c
salt=$(echo $var | wc -c)

done

if [[ ! -z "$salt" ]]
then
    decrypt
    echo $flag
else
    exit 1
fi

```

And here is the output I got

```shell-session
“Try number 0”
5
“Try number 1”
9
“Try number 2”
13
“Try number 3”
21
“Try number 4”
29
“Try number 5”
41
“Try number 6”
57
“Try number 7”
77
“Try number 8”
106
“Try number 9”
146
“Try number 10”
199
“Try number 11”
272
“Try number 12”
369
“Try number 13”
499
“Try number 14”
677
“Try number 15”
916
“Try number 16”
1241
“Try number 17”
1678
“Try number 18”
2270
“Try number 19”
3068
“Try number 20”
4146
“Try number 21”
5601
“Try number 22”
7567
“Try number 23”
10225
“Try number 24”
13816
“Try number 25”
18667
“Try number 26”
25220
“Try number 27”
34071
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
HTBL00p5r0x
```

Booyah. `HTBL00p5r0x`.

## Flow Control - Branches

As we have already seen, the branches in flow control include `if-else` and the `case` statements. We have already discussed the `if-else` statements in detail and know how this works. Now we will take a closer look at the case statements.

### Case Statements

- Switch case
  
  - Compares variable with `exact value`

- If-else
  
  - Check `Boolean`

#### Syntax - Switch-Case

```bash
case <expression> in
    pattern_1 ) statements ;;
    pattern_2 ) statements ;;
    pattern_3 ) statements ;;
esac
```

We need double semicolons for statements to work

#### CIDR.sh

```bash
<SNIP>
# Available options
echo -e "Additional options available:"
echo -e "\t1) Identify the corresponding network range of target domain."
echo -e "\t2) Ping discovered hosts."
echo -e "\t3) All checks."
echo -e "\t*) Exit.\n"

read -p "Select your option: " opt

case $opt in
    "1") network_range ;;
    "2") ping_host ;;
    "3") network_range && ping_host ;;
    "*") exit 0 ;;
esac
<SNIP>
```
# Execution Flow

## Functions



#### Method 1 - Functions

```bash
function name {
    <commands>
}
```

#### Method 2 - Functions

```bash
name() {
    <commands>
}
```

#### CIDR.sh

```bash
<SNIP>
# Identify Network range for the specified IP address(es)
function network_range {
    for ip in $ipaddr
    do
        netrange=$(whois $ip | grep "NetRange\|CIDR" | tee -a CIDR.txt)
        cidr=$(whois $ip | grep "CIDR" | awk '{print $2}')
        cidr_ips=$(prips $cidr)
        echo -e "\nNetRange for $ip:"
        echo -e "$netrange"
    done
}
<SNIP>
```

#### Function Execution - CIDR.sh

```bash
<SNIP>
case $opt in
    "1") network_range ;;
    "2") ping_host ;;
    "3") network_range && ping_host ;;
    "*") exit 0 ;;
esac
```

### Parameter Passing

Passing through `$1` - `$9` (`${n}`), or `$variable`

#### PrintPars.sh

```bash
#!/bin/bash

function print_pars {
    echo $1 $2 $3
}

one="First parameter"
two="Second parameter"
three="Third parameter"

print_pars "$one" "$two" "$three"
```

#### PrintPars.sh

```shell-session
DanielBoye@htb[/htb]$ ./PrintPars.sh

First parameter Second parameter Third parameter
```

## Return Values



| **Return Code** | **Description**                |
| --------------- | ------------------------------ |
| `1`             | General errors                 |
| `2`             | Misuse of shell builtins       |
| `126`           | Command invoked cannot execute |
| `127`           | Command not found              |
| `128`           | Invalid argument to exit       |
| `128+n`         | Fatal error signal "`n`"       |
| `130`           | Script terminated by Control-C |
| `255\*`         | Exit status out of range       |

#### Return.sh

```bash
#!/bin/bash

function given_args {

        if [ $# -lt 1 ]
        then
                echo -e "Number of arguments: $#"
                return 1
        else
                echo -e "Number of arguments: $#"
                return 0
        fi
}

# No arguments given
given_args
echo -e "Function status code: $?\n"

# One argument given
given_args "argument"
echo -e "Function status code: $?\n"

# Pass the results of the funtion into a variable
content=$(given_args "argument")

echo -e "Content of the variable: \n\t$content"
```

```shell-session
DanielBoye@htb[/htb]$ ./Return.sh

Number of arguments: 0
Function status code: 1

Number of arguments: 1
Function status code: 0

Content of the variable:    
Number of arguments: 1
```

## Debugging

Bash allows us to debug our code by using the "`-x`" (`xtrace`) and "`-v`" options. Now let us see an example with our `CIDR.sh` script.



### CIDR.sh - Debugging

```shell-session
DanielBoye@htb[/htb]$ bash -x CIDR.sh

+ '[' 0 -eq 0 ']'+ echo -e 'You need to specify the target domain.\n'You need to specify the target domain.+ echo -e Usage:Usage:+ echo -e '\tCIDR.sh <domain>'    CIDR.sh <domain>+ exit 1
```



### CIDR.sh - Verbose Debugging

`-v` for verbose Debugging



```bash
DanielBoye@htb[/htb]$ bash -x -v CIDR.sh

#!/bin/bash

# Check for given argument
if [ $# -eq 0 ]
then
	echo -e "You need to specify the target domain.\n"
	echo -e "Usage:"
	echo -e "\t$0 <domain>"
	exit 1
else
	domain=$1
fi
+ '[' 0 -eq 0 ']'
+ echo -e 'You need to specify the target domain.\n'
You need to specify the target domain.

+ echo -e Usage:
Usage:
+ echo -e '\tCIDR.sh <domain>'
	CIDR.sh <domain>
+ exit 1
```