# Practicing Piping

### Redirecting output
```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{ciY17TtcREHC-PgPR_1kQD9UpDz.dRjN1QDLzMTN2czW}
```
Redirected the output of ```echo PWN`` to ```COLLEGE``` to get the flag **pwn.college{ciY17TtcREHC-PgPR_1kQD9UpDz.dRjN1QDLzMTN2czW}**.

### Redirecting more output
```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{oOhuS1i7WhaSMhsOvRLKte8llX5.dVjN1QDLzMTN2czW}
```
Redirected the output of ```/challenge/run``` to ```myflag``` and then used ```cat``` to get the flag **pwn.college{oOhuS1i7WhaSMhsOvRLKte8llX5.dVjN1QDLzMTN2czW}**.

### Appending output
```
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{YMMRWb1PT9obv5q9UDMxbioqvXE.ddDM5QDLzMTN2czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
```
Appended the output of ```/challenge/run``` to ```/home/hacker/the-flag``` and then used ```cat``` to get the flag **pwn.college{YMMRWb1PT9obv5q9UDMxbioqvXE.ddDM5QDLzMTN2czW}**.

### Redirecting errors
```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{c_BwnZK8mwZXHUkIMJd4AIbUtMO.ddjN1QDLzMTN2czW}
```
Redirected stdout of ```/challenge/run``` to ```myflag``` and sterr to ```instructions```, then used ```cat``` to get the flag **pwn.college{c_BwnZK8mwZXHUkIMJd4AIbUtMO.ddjN1QDLzMTN2czW}**.

### Redirecting input
```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{4wcMUdI3811lBg7ew9NBmkDvVw2.dBzN1QDLzMTN2czW}
```
Redirected output of ```echo COLLEGE``` to ```PWN``` then redirected it as input to ```/challenge/run``` to get the flag **pwn.college{4wcMUdI3811lBg7ew9NBmkDvVw2.dBzN1QDLzMTN2czW}**.

### Grepping stored results
```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college < /tmp/data.txt
pwn.college{oMYotEQPZKMO4nxXAIL6bV-Oxfh.dhTM4QDLzMTN2czW}
```
Redirected output of ```/challenge/run``` to ```/tmp/data.txt``` then redirected it as input to ```grep``` command to find the string pwn.college. Got the flag **pwn.college{oMYotEQPZKMO4nxXAIL6bV-Oxfh.dhTM4QDLzMTN2czW}**.

### Grepping live output
```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{cwb-rRze6zVgqDzg0H0S4h3I-BX.dlTM4QDLzMTN2czW}
```
Piped output of ```/challenge/run``` into ```grep``` command to find the string pwn.college using | ( _pipe operator_ that connects standard output from the command to the left of the pipe to the command pn the right of it) to get the flag **pwn.college{cwb-rRze6zVgqDzg0H0S4h3I-BX.dlTM4QDLzMTN2czW}**.

### Grepping errors
```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{IWlTwL6B2M9KshDvOUh1jWLBYDC.dVDM5QDLzMTN2czW}
```
Redirected stderr (fd 2) of ```/challenge/run``` into stdout (fd1) using  &> operator and then pipped it into ```grep``` command to find the string pwn.college to get the flag **pwn.college{IWlTwL6B2M9KshDvOUh1jWLBYDC.dVDM5QDLzMTN2czW}**.

### Duplicating piped data with tee
```
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee T | /challenge/college
Processing...
The input to 'college' does not contain the correct secret code! This code 
should be provided by the 'pwn' command. HINT: use 'tee' to intercept the 
output of 'pwn' and figure out what the code needs to be.
hacker@piping~duplicating-piped-data-with-tee:~$ cat T
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "krHXIlYz"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret krHXIlYz | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{krHXIlYzsXQTqlAvOt_BofMXZG0.dFjM5QDLzMTN2czW}
```
Used ```tee``` command to save output of ```/challenge/pwn``` file to ```T``` file as well as pass it on to ```/challenge/college```. Read ```T``` to find the correct argument for finding the flag **pwn.college{krHXIlYzsXQTqlAvOt_BofMXZG0.dFjM5QDLzMTN2czW}**.

### Writing to multiple programs
```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the) >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and 
/challenge/planet. Don't try to copy-paste it; it changes too fast.
3898177332181622879
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{gAsU16eHhZyk8yrMYgn8PyqxeUe.dBDO0UDLzMTN2czW}
```
_Process substitution_ allows a process’s input or output to be referred to using a filename, taking the form of _>(command)_ or _<(command)_.

Redirected output of ```/challenge/hack``` into named pipes ```>(/challenge/the)``` and ```>(/challenge/planet)``` using ```tee``` as it has the ability to write into multiple files at once to get the flag **pwn.college{gAsU16eHhZyk8yrMYgn8PyqxeUe.dBDO0UDLzMTN2czW}**.

### Split-piping stderr and stdout
```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack 2> >(/challenge/the) > >(/challenge/planet)
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{wUhGXNRcuF3MKlwYDaMD5HcCcFJ.dFDNwYDLzMTN2czW}
```
Redirected stderr of ```/challenge/hack``` into named pipe ```>(/challenge/the)``` and srdout into ```>(/challenge/planet)``` using redirection operators to get the flag **pwn.college{wUhGXNRcuF3MKlwYDaMD5HcCcFJ.dFDNwYDLzMTN2czW}**.
___