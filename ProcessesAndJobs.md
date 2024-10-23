# Processes and Jobs

### Listing Processes
```
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 12:05 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/default/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 12:05 ?        00:00:00 /run/dojo/bin/sleep 6h
root          68       1  0 12:05 ?        00:00:00 /challenge/29086-run-18394
root          72      68  0 12:05 ?        00:00:00 sleep 6h
hacker        81       1  5 12:05 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-c
hacker       102      81 34 12:05 ?        00:00:05 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-c
hacker       143     102 15 12:05 ?        00:00:01 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node --dns-result-order=ipv4first /nix/store/3v4hd
hacker       154     102  5 12:05 ?        00:00:00 /nix/store/bmmjbvb8hishfrg78ygjlynpq3ikpl39-nodejs-20.15.1/bin/node /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-c
hacker       165     154  0 12:05 pts/0    00:00:00 /run/dojo/bin/bash --init-file /nix/store/3v4hdb2gmpj7jv2z848ikakhzl9rjgwh-code-server/libexec/code-server/lib/vs
hacker       216     165  0 12:05 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/29086-run-18394
Yahaha, you found me! Here is your flag:
pwn.college{ky_t0MRAv_ZGZRZyQ4KECcoqIDN.dhzM4QDLzMTN2czW}
Now I will sleep for a while (so that you could find me with 'ps').
```
The ```ps``` command ("process snapshot" or "process status") lists all the running processes on the terminal. 

We can use "Standard" Syntax:
- -e to list "every" process 
- -f for a "full format" output, including arguments. 

These can be combined into a single argument -ef.

Alternatively, we can use "BSD" Syntax:
- a to list processes for all users
- x to list processes that aren't running in a terminal
- u for a "user-readable" output.
  
These can be combined into a single argument aux.

Used ```ps -ef``` to get the flag **pwn.college{ky_t0MRAv_ZGZRZyQ4KECcoqIDN.dhzM4QDLzMTN2czW}**.

### Killing Processes
```
hacker@processes~killing-processes:~$ ps -ef | grep /challenge/dont_run
hacker        73      71  0 15:55 ?        00:00:00 /challenge/dont_run
hacker       557     475  0 15:57 pts/1    00:00:00 grep --color=auto /challenge/dont_run
hacker@processes~killing-processes:~$ kill 73
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{MYCS4EnfahfBYjG1KZRhnPa72Mp.dJDN4QDLzMTN2czW}
```
Used ```kill``` to terminate ```/challenge/dont_run``` command by passing the process identifier, i.e. the PID found from ps using grep, as an argument to get the flag **pwn.college{MYCS4EnfahfBYjG1KZRhnPa72Mp.dJDN4QDLzMTN2czW}**.

### Interrupting Processes
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{M_EFW0RGm3Fe41QsVI1WHd_R60x.dNDN4QDLzMTN2czW}
```
Ctrl-C is a hotkey that sent an "interrupt" to ```/challenge/run``` waiting on input from the terminal (typically, this causes the application to cleanly exit) to get the flag **pwn.college{M_EFW0RGm3Fe41QsVI1WHd_R60x.dNDN4QDLzMTN2czW}**.

### Suspending Processes
```
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         313     207  0 16:00 pts/0    00:00:00 bash /challenge/run
root         315     313  0 16:00 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         313     207  0 16:00 pts/0    00:00:00 bash /challenge/run
root         377     207  0 16:00 pts/0    00:00:00 bash /challenge/run
root         379     377  0 16:00 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{ouOxmmOCUjIOKLA4gzqY8Ekissg.dVDN4QDLzMTN2czW}
```
Suspended ```/challenge/run``` to the background with Ctrl-Z, then launched it again to get the flag **pwn.college{ouOxmmOCUjIOKLA4gzqY8Ekissg.dVDN4QDLzMTN2czW}**.

### Resuming Processes
```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg 
/challenge/run
I'm back! Here's your flag:
pwn.college{kOOFdEVYfWlzTX7QbyVdqzhG269.dZDN4QDLzMTN2czW}
Don't forget to press Enter to quit me!

Goodbye!
```
Suspended ```/challenge/run``` to the background with Ctrl-Z, then resumed it using ```fg``` to get the flag **pwn.college{kOOFdEVYfWlzTX7QbyVdqzhG269.dZDN4QDLzMTN2czW}**.

### Backgrounding Processes
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         274 S+   bash /challenge/run
root         276 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         274 S    bash /challenge/run
root         328 S    sleep 6h
root         379 S+   bash /challenge/run
root         381 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{AEM1vFjyiZbMpWqX3JX49_5xfz6.ddDN4QDLzMTN2czW}
```
Suspended ```/challenge/run``` to the background with Ctrl-Z, then resumed it in the backgroud using ```bg``` and launched a copy, running simultaneously, to get the flag.

### Foregrounding Processes
```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &



Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.
hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{QhQZS2OuyK-hFtEG5vqbAcqS5uj.dhDN4QDLzMTN2czW}
```
Suspended ```/challenge/run``` to the background with Ctrl-Z, resumed it in the backgroud using ```bg```, and then foregrounded it using ```fg``` to get the flag **pwn.college{QhQZS2OuyK-hFtEG5vqbAcqS5uj.dhDN4QDLzMTN2czW}**.

### Starting Backgrounded Processes
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 318



Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{MejQPtoknGQ-K1QVjEkuGp88xhf.dlDN4QDLzMTN2czW}
[1]+  Done                    /challenge/run
```
Launched ```/challenge/run``` with an appended & _(background operator)_ directly in the background to get the flag **pwn.college{MejQPtoknGQ-K1QVjEkuGp88xhf.dlDN4QDLzMTN2czW}**.

### Process Exit Codes
```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
127
hacker@processes~process-exit-codes:~$ /challenge/submit-code 127
CORRECT! Here is your flag:
pwn.college{QMONrU0Hq_29gTlQzzlpvpizUSr.dljN4UDLzMTN2czW}
```
Every shell command, including every program and every builtin, exits with an exit code when it finishes running and terminates. Commands that succeed typically return 0 and commands that fail typically return a non-zero value, most commonly 1 but sometimes an error code that identifies a specific failure mode.

Retrieved the exit code returned by ```/challenge/get-code``` using ? variable prepended with $ to read its value and subsequently ran ```/challenge/submit-code``` with that error code as an argument to get the flag **pwn.college{QMONrU0Hq_29gTlQzzlpvpizUSr.dljN4UDLzMTN2czW}**.
___