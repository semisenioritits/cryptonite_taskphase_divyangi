# File Globbing

### Matching with *
```
hacker@globbing~matching-with-:~$ ls /
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{gmrxLUIRU0IxvFb5q1CEJpSAsZ9.dFjM4QDLzMTN2czW}
```
\* is a wildcard that tries to replace an argument with any files that match the pattern.
  
Used ```cd /ch*``` command to change to ```/challenge``` directory as the challenge required the argument to be atmost 4 characters and there's no other directory in ```/``` starting with ch. Invoked ```/challenge/run``` to get the flag **pwn.college{gmrxLUIRU0IxvFb5q1CEJpSAsZ9.dFjM4QDLzMTN2czW}**.

### Matching with ?
```
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ ./run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{Ee1kuwFITkHLaEiox03yx3YYSX3.dJjM4QDLzMTN2czW}
```
The shell treats ? as  a single-character wildcard. It works like *, but only matches one character.

Used ```cd /?ha??enge``` command as per the challenge description and then invoked ```./run``` to get the flag **pwn.college{Ee1kuwFITkHLaEiox03yx3YYSX3.dJjM4QDLzMTN2czW}**.

### Matching with []
```
hacker@globbing~matching-with-:/challenge/files$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{4bmdyHMJaWGBaRx121sBELZ_Kty.dNjM4QDLzMTN2czW}
```
[] is a wildcard for some subset of potential characters, specified within the brackets.
 
Changed  into ```/challenge/files``` directory and then used [] to only run file_b, file_a, file_s and file_h to get the flag **pwn.college{4bmdyHMJaWGBaRx121sBELZ_Kty.dNjM4QDLzMTN2czW}**.

### Matching paths with []
```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{cHkgUziC7_xAuHoYtXQojlBfnna.dRjM4QDLzMTN2czW}
```
Use:
- / to search
- n to move to the next result
- N to return to the previous result
- ?to search backwards

Used [] to only run file_b, file_a, file_s and file_h using absolute paths to get the flag **pwn.college{cHkgUziC7_xAuHoYtXQojlBfnna.dRjM4QDLzMTN2czW}**.

### Mixing globs
```
hacker@globbing~mixing-globs:/challenge/files$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ ls
amazing    challenging  educational  great  incredible  kind      magical  optimistic  queenly  splendid   uplifting   wonderful  youthful
beautiful  delightful   fantastic    happy  jovial      laughing  nice     pwning      radiant  thrilling  victorious  xenial     zesty
hacker@globbing~mixing-globs:/challenge/files$ ../run [cep]*
You got it! Here is your flag!
pwn.college{0a2cqMnw1bGY-IknkZ53EATa3zc.dVjM4QDLzMTN2czW}
```
Changed into ```/challenge/files``` and used ```ls```, concluding no other files start with the letters c, e and p, so I used the glob [cep]* to match with all the files in ```/challenge/files``` that start with those letters to get the flag **pwn.college{0a2cqMnw1bGY-IknkZ53EATa3zc.dVjM4QDLzMTN2czW}**.

### Exclusionary globbing
```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{ktaGCy49-FY4bU_E2yrMRCDgzmq.dZjM4QDLzMTN2czW}
```
If the first character in [] is a ! or ^, the glob inverts, matching characters that aren't listed.

Used ! to match with file names not starting from the letters p, w and n to get the flag **pwn.college{ktaGCy49-FY4bU_E2yrMRCDgzmq.dZjM4QDLzMTN2czW}**.
___