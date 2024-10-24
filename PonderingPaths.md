# Pondering Paths

### The Root
```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{0o2MCqXbk1vCIuerHwBLd5Nfflq.dhzN5QDLzMTN2czW}
```
Invoked the ```pwn``` command using its absolute path to get the flag **pwn.college{0o2MCqXbk1vCIuerHwBLd5Nfflq.dhzN5QDLzMTN2czW}**.

### Program and absolute paths
```
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{gM9TDWUu1VtU18rQID71ygF4ybv.dVDN1QDLzMTN2czW}
```
Invoked the ```run``` command in ```challenge``` directory, which in turn is in ```/``` directory, using its absolute path to get the flag **pwn.college{gM9TDWUu1VtU18rQID71ygF4ybv.dVDN1QDLzMTN2czW}**.

### Position thy self
```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /var directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /var
hacker@paths~position-thy-self:/var$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{UQY3mhRi_OHZaT_Pqm1sdoH3lkU.dZDN1QDLzMTN2czW}
```
Invoked ```/challenge/run``` to find which directory to run it from, then used ```cd``` command to change into ```/var``` directory and invoked ```/challenge/run``` again there to get the flag **pwn.college{UQY3mhRi_OHZaT_Pqm1sdoH3lkU.dZDN1QDLzMTN2czW}**.

### Position elsewhere
```
hacker@paths~position-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var/lib/apt/lists directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-elsewhere:~$ cd /var/lib/apt/lists
hacker@paths~position-elsewhere:/var/lib/apt/lists$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{YWu1nduokqBXbY3WaGr6Hct3WkN.ddDN1QDLzMTN2czW}
```
Invoked ```/challenge/run``` to find which directory to run it from, then used ```cd``` command to change into ```/var/lib/apt/lists``` directory and invoked ```/challenge/run``` again there to get the flag **pwn.college{YWu1nduokqBXbY3WaGr6Hct3WkN.ddDN1QDLzMTN2czW}**.

### Position yet elsewhere
```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /usr/include directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /usr/include
hacker@paths~position-yet-elsewhere:/usr/include$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{QcofvhfOHwqlN7-G9ywGkXHdL7C.dhDN1QDLzMTN2czW}
```
Invoked ```/challenge/run``` to find which directory to run it from, then used ```cd``` command to change into ```/usr/include``` directory and invoked ```/challenge/run``` again there to get the flag **pwn.college{QcofvhfOHwqlN7-G9ywGkXHdL7C.dhDN1QDLzMTN2czW}**.

### implicit relative paths, from /
```
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{A2ac03IKWEbvp0OmAt_g6wRWFZ3.dlDN1QDLzMTN2czW}
```
Changed to ```/``` directory to invoke ```challenge/run``` using its relative path to get the flag **pwn.college{A2ac03IKWEbvp0OmAt_g6wRWFZ3.dlDN1QDLzMTN2czW}**.

### explicit relative paths, from /
```
hacker@paths~explicit-relative-paths-from-:~$ cd /
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Y8YDl06IQKSNOekFXFiUOE5793O.dBTN1QDLzMTN2czW}
```
In most operating systems, including Linux, every directory has two implicit entries that one can reference in paths: . and ... The first, ., refers right to the same directory, so the following absolute paths are all identical to each other:

- /challenge
- /challenge/.
- /challenge/././././././././.
  
The latter refers to the parent directory.

Changed to ```/``` directory to invoke ```./challenge/run``` using its explicit relative path to get the flag **pwn.college{Y8YDl06IQKSNOekFXFiUOE5793O.dBTN1QDLzMTN2czW}**.

### implicit relative path
```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{0PqNU5fUqQtiH-ix3yi_e-BVH6W.dFTN1QDLzMTN2czW}
```
Changed to ```/challenge``` directory to invoke ```./run``` using its explicit relative path to get the flag **pwn.college{0PqNU5fUqQtiH-ix3yi_e-BVH6W.dFTN1QDLzMTN2czW}**.

Linux explicitly avoids automatically looking in the current directory when provided a "naked" path. This is a safety measure: if Linux searched the current directory for programs every time a naked path is entered, one could accidentally execute programs in the current directory that happened to have the same names as core system utilities.

```
@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ run
bash: run: command not found
```

### home sweet home
```
hacker@paths~home-sweet-home:~$ /challenge/run ~/f
Writing the file to /home/hacker/f!
... and reading it back to you:
pwn.college{gJFu5V70y257jNpw089uBiFLjOH.dNzM4QDLzMTN2czW}
```
Used ```~/f``` file as an argument for ```/challenge/run``` as the challenge needed the argument to be an absolute path inside the ```home``` directory and argument length atmost 3 characters. Got the flag**pwn.college{gJFu5V70y257jNpw089uBiFLjOH.dNzM4QDLzMTN2czW}**.
___