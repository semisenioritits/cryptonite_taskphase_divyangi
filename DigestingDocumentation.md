# Comprehending Commands

### Learning From Documentation
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{ktVK2dFkSwS0TmjhHRjGeV-4Dsx.dRjM5QDLzMTN2czW}
```
Invoked the ```/challenge/challenge``` command with --giveflag argument get the flag **pwn.college{ktVK2dFkSwS0TmjhHRjGeV-4Dsx.dRjM5QDLzMTN2czW}**.

### Learning Complex Usage
```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{8hwuTs8C3dJgSvRPIpRMmNJxYHl.dVjM5QDLzMTN2czW}
```
Invoked the ```/challenge/challenge``` command with --printfile argument that takes ```/flag``` argument get the flag **pwn.college{8hwuTs8C3dJgSvRPIpRMmNJxYHl.dVjM5QDLzMTN2czW}**.

### Reading Manuals
```
hacker@man~reading-manuals:~$ man challenge

CHALLENGE(1)                                                           Challenge Commands                                                           CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --spkeud NUM
              print the flag if NUM is 574

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
hacker@man~reading-manuals:~$ /challenge/challenge --spkeud 574
Correct usage! Your flag: pwn.college{sSV_JQpHkeud5MXGZqtEGMQAM7n.dRTM4QDLzMTN2czW}
```
 ```man``` is short for manual, and will display (if available) the manual of the command passed as an argument. Use: 
 - arrow keys and PgUp/PgDn to scroll around the manpage
 - q to quit.
 
 Used ```man``` to find the argument --spkeud 574 that prints the flag **pwn.college{sSV_JQpHkeud5MXGZqtEGMQAM7n.dRTM4QDLzMTN2czW}**.

### Searching Manuals
```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --da
Initializing...
Correct usage! Your flag: pwn.college{UlrYmaQOHI90VvP9JP9-Uyp1sVT.dVTM4QDLzMTN2czW}
```
Use:
- / to search
- n to move to the next result
- N to return to the previous result
- ?to search backwards

Used / key to search the string flag in man page of  ```challenge``` to find the argument --da to print the flag **pwn.college{UlrYmaQOHI90VvP9JP9-Uyp1sVT.dVTM4QDLzMTN2czW}**.

### Searching For Manuals
```
hacker@man~searching-for-manuals:~$ man -k challenge
otbqfinayr (1)       - print the flag!
hacker@man~searching-for-manuals:~$ man otbqfinayr

CHALLENGE(1)                                                    Challenge Commands                                                   CHALLENGE(1)

NAME
       /challenge/challenge - print the flag!

SYNOPSIS
       challenge OPTION

DESCRIPTION
       Output the flag when called with the right arguments.

       --fortune
              read a fortune

       --version
              output version information and exit

       --otbqfi NUM
              print the flag if NUM is 694

AUTHOR
       Written by Zardus.

REPORTING BUGS
       The repository for this dojo: <https://github.com/pwncollege/linux-luminarium/>

SEE ALSO
hacker@man~searching-for-manuals:~$ /challenge/challenge --otbqfi 694
Correct usage! Your flag: pwn.college{ot6bTF9MqJf4inI4ayrGSsEQg12.dZTM4QDLzMTN2czW}
```
Used ```man -k``` to search all man page descriptions for keyword challenge. After finding the name of challenge's man page, used ```man otbqfinayr``` command to find the argument to print the flag **pwn.college{ot6bTF9MqJf4inI4ayrGSsEQg12.dZTM4QDLzMTN2czW}**.

### Helpful Programs
```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune] [-v] [-g GIVE_THE_FLAG] [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct value
  -p, --print-value     print the value that will cause the -g option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 240
hacker@man~helpful-programs:~$ /challenge/challenge -g 240
Correct usage! Your flag: pwn.college{gZZONklM2JIldZN4Xx0wV3U1-xA.ddjM4QDLzMTN2czW}
```
Used --help argument to find the arguments to get the flag **pwn.college{gZZONklM2JIldZN4Xx0wV3U1-xA.ddjM4QDLzMTN2czW}**.

### Help for Builtins
```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!
    
    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "ki0c484Q".
hacker@man~help-for-builtins:~$ challenge --secret ki0c484Q
Correct! Here is your flag!
pwn.college{ki0c484QoyRut7_Ld0PO051sDYv.dRTM5QDLzMTN2czW}
```
Some commands, rather than being programs with man pages and help options, are built into the shell itself. These are called _builtins_. Builtins are invoked just like commands, but the shell handles them internally instead of launching other programs. One can get a list of shell builtins by running the builtin ```help```.

Used ```help``` builtin to print all arguments of ```challenge``` and then used --secret argument to get the flag **pwn.college{ki0c484QoyRut7_Ld0PO051sDYv.dRTM5QDLzMTN2czW}**.
___