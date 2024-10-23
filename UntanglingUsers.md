# Untangling Users

### Becoming root with su
```
hacker@users~becoming-root-with-su:~$ su
Password: 
root@users~becoming-root-with-su:/home/hacker# cat /flag
pwn.college{w4KrVKeOxP4yEYr--S1qwGC6eR-.dVTN0UDLzMTN2czW}
```
Used ```su``` (the switch user command) to switch to ```root``` user using the given password "hack-the-planet" and ran ```/challenge/run``` to get the flag **pwn.college{w4KrVKeOxP4yEYr--S1qwGC6eR-.dVTN0UDLzMTN2czW}**.

### Other users with su
```
hacker@users~other-users-with-su:~$ su zardus
Password: 
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{MFbCTZN8H8YNRyG4PayFHb1QwoS.dZTN0UDLzMTN2czW}
```
Used ```su``` (the switch user command) to switch to ```zardeus``` user using the given password "dont-hack-me" and used ```cat /flag``` to get the flag **pwn.college{MFbCTZN8H8YNRyG4PayFHb1QwoS.dZTN0UDLzMTN2czW}**.

### Cracking passwords
```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:24 100% 2/3 0.04152g/s 241.8p/s 241.8c/s 241.8C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password: 
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{8CSmvxcdCM5v5M5Ef4TfyOfuYQy.ddTN0UDLzMTN2czW}
```
When one inputs a password into su, it one-way-encrypts (hashes) it and compares the result against the stored value in /etc/shadow. If the result matches, su grants you access to the user.

Used John the Ripper tool on given leak of ```/etc/shadow``` in ```/challenge/shadow-leak``` to su to zardus using password "aardvark", then ran ```/challenge/run``` to get the flag **pwn.college{8CSmvxcdCM5v5M5Ef4TfyOfuYQy.ddTN0UDLzMTN2czW}**.

### Using sudo
```
hacker@users~using-sudo:~$ sudo cat /flag
pwn.college{QXR98GJ2vUYMwfV-yafPAoKzkiB.dhTN0UDLzMTN2czW}
```
Unlike su, which defaults to launching a shell as a specified user, sudo defaults to running a command as root:

```
hacker@dojo:~$ whoami
hacker
hacker@dojo:~$ sudo whoami
root
```

Rather than authenticating via password, sudo relies on policies that it checks to determine the user's authorization run things as root. These policies are defined in ```/etc/sudoers```.

Used sudo to run ```cat /flag``` as administrator to get the flag **pwn.college{QXR98GJ2vUYMwfV-yafPAoKzkiB.dhTN0UDLzMTN2czW}**.
___