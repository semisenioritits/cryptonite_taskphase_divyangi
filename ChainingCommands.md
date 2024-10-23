# Chaining Commands

### Chaining with Semicolons
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{ABNqh8vD6FyhKkSxJAC5BHqN6mZ.dVTN4QDLzMTN2czW}
```
Chained commands ```/challenge/pwn``` and ``/challenge/college`` together using ; _(command separator)_ to get the flag **pwn.college{ABNqh8vD6FyhKkSxJAC5BHqN6mZ.dVTN4QDLzMTN2czW}**.

### Your First Shell Script
```
hacker@practice~chaining~your-first-shell-script:~$ touch x.sh
hacker@practice~chaining~your-first-shell-script:~$ vim x.sh
hacker@practice~chaining~your-first-shell-script:~$ cat x.sh
/challenge/pwn
/challenge/college
hacker@practice~chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{IXBTQMqxStuJZRCsX8xTqSet4DG.dFzN4QDLzMTN2czW}
```
Used ```vim``` to put the commands ```/challenge/pwn``` and ``/challenge/college`` into file (_shell script_) x.sh then launched it using ```bash``` command to get the flag **pwn.college{IXBTQMqxStuJZRCsX8xTqSet4DG.dFzN4QDLzMTN2czW}**.

### Redirecting Script Output
```
hacker@chaining~redirecting-script-output:~$ touch x.sh; vim x.sh
hacker@chaining~redirecting-script-output:~$ cat x.sh
/challenge/pwn
/challenge/college
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{MC9nhk-Ue80dNrVDss1SIig0yZo.dhTM5QDLzMTN2czW}
```
Used ```vim``` to put the commands ```/challenge/pwn``` and ``/challenge/college`` into file (_shell script_) x.sh, then piped the output of ```bash x.sh``` into ```/challenge/solve``` to get the flag **pwn.college{MC9nhk-Ue80dNrVDss1SIig0yZo.dhTM5QDLzMTN2czW}**.

### Executable Shell Scripts
```
hacker@chaining~executable-shell-scripts:~$ touch x.sh; vim x.sh
hacker@chaining~executable-shell-scripts:~$ cat x.sh
/challenge/solve
hacker@chaining~executable-shell-scripts:~$ ls -l x.sh
-rw-r--r-- 1 hacker hacker 18 Oct 22 23:38 x.sh
hacker@chaining~executable-shell-scripts:~$ chmod u+x x.sh
hacker@chaining~executable-shell-scripts:~$ ./x.sh
Congratulations on your shell script execution! Your flag:
pwn.college{UhPZC72p5TK1rNCjXz1Y_X5GHsh.dRzNyUDLzMTN2czW}
```
Used ```vim``` to put the command ```/challenge/solve``` into file (_shell script_) x.sh, changed permissions of x.sh so as to make it executable using ```chmod u+x``` and executed it to get the flag **pwn.college{UhPZC72p5TK1rNCjXz1Y_X5GHsh.dRzNyUDLzMTN2czW}**.
___