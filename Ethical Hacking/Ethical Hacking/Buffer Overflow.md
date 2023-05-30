
## Introduction

buffer overflow happens because of careless code.specially in C and C++ because, that languages does not automatically prevent buffer overflow.මේක නිසා developers අමතර අවදානයක් මේ සම්බන්දව දිය යුතුයි. java වලදි garbage collector තියෙන නිසා java buffer overflow සිදුවීමේ අඩු සම්බාවිතාවක් පමනක් ඇත. 

![[Pasted image 20230519141617.png]]  
![[Pasted image 20230519141639.png]]  

### text 
මේක resad only part එකකි .මෙකෙ තියෙන්නෙ  programme එකට අදාල  assembler instructions ය .මේක වෙනස් කරන්න බැලුවොත් segmentation fault එකක් විය හැක.

### data 
මෙහිදී global සහ static variables තියයි.

### data
ගොඩක් compilers සහ linkers මේ section එක බාවිතා කරයි.data section එකෙ part එකකි.0 bits වලින් represent කරන static variables ඇත.

### Heap 
The heap is a memory used by programming languages to store global variables. By default, all global variable are stored in heap memory space. It supports Dynamic memory allocation.

The heap is not managed automatically for you and is not as tightly managed by the CPU. It is more like a free-floating region of memory.

static variables වල values මෙහිදී තබයි.

### stack
A stack is a special area of computer’s memory which stores temporary variables created by a function. In stack, variables are declared, stored and initialized during runtime.

It is a temporary storage memory. When the computing task is complete, the memory of the variable will be automatically erased. The stack section mostly contains methods, local variable, and reference variables.

🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠🤠

programme එකකින් A ගොඩක් input කරොත් epi එකට A එකෙ hexadecimal number එක තියෙනවනම් ඒක (41414141) buffer overflow එක sucess.

77-94
## setup

☠️first you need a vulnerable machine and a attacker machine.

- a windows machine(you can use your main OS.)
👉next we want to download 2 things :

1️⃣ vulnserver
2️⃣ immunity debuger => this is for see whats going on while attacking.

- vulnserver එක extract කරගන්න දැනට install කරන්න එපා.
- immunity debugger එක install කරගන්න.

### virus protection එක off කරන්න.

✔ දැන් vulnserver eka install කරන්න (run as administer)
😍 දැන් immunity debugger එකත් administrator විදිහටර් run කරන්න.

_default vulnserver run in port 9999_
 