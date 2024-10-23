# Shell Variables

### Printing Variables
```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{gkqHUeTAJA4EcnWgXgwf7KSGhzn.ddTN1QDLzMTN2czW}
```
The ```echo``` command prints out the value of FLAG variable as it's prepended by $ symbol. Got the flag **pwn.college{gkqHUeTAJA4EcnWgXgwf7KSGhzn.ddTN1QDLzMTN2czW}**.

### Setting Variables
```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wqJ6Apw1-Yb4m1ZC5j_6wENWgyP.dlTN1QDLzMTN2czW}
```
The = symbol sets the value of PWN to COLLEGE, which printed out the flag. Got the flag **pwn.college{wqJ6Apw1-Yb4m1ZC5j_6wENWgyP.dlTN1QDLzMTN2czW}**.

### Multi-word Variables
```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{Q3CRe-0iJblp8YDSwvknN8-dq6A.dBjN1QDLzMTN2czW}
```
The quote marks are required setting multi-word variable values as when the shell sees a space, it ends the variable assignment and interprets the next word as a command.

Set the value of PWN to "COLLEGE YEAH" to get the flag **pwn.college{Q3CRe-0iJblp8YDSwvknN8-dq6A.dBjN1QDLzMTN2czW}**.

### Exporting Variables
```
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great 
job! Here is your flag:
pwn.college{4V5h2BsD8C25yw6WlQt45OMTsv-.dJjN1QDLzMTN2czW}
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
```
The challenge required passing the value COLLEGE to PWN variable and exporting it and settig the value of COLLEGE variable to PWN without exporting it to get the flag **pwn.college{4V5h2BsD8C25yw6WlQt45OMTsv-.dJjN1QDLzMTN2czW}**.

When variables are exported, they are passed into the environment variables of child processes, which then can use the values. Shell variables, on the other hand are available only in the current shell session and not passed to child processes unless exported.
```
hacker@variables~exporting-variables:~$ env | grep PWN
PWN=COLLEGE
```

### Printing Exported Variables
```
hacker@variables~printing-exported-variables:~$ env | grep FLAG
FLAG=pwn.college{0uJYX1xCE1Rimzqpzge2kqbiwDX.dhTN1QDLzMTN2czW}
```
Piped the output of ```env``` command to ```grep``` to find the environment variable named FLAG with value **pwn.college{0uJYX1xCE1Rimzqpzge2kqbiwDX.dhTN1QDLzMTN2czW}**.

### Storing Command Output
```
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out 
and submit it!
hacker@variables~storing-command-output:~$ echo $PWN
pwn.college{g9JEVJYIkKf9m4pjf2WJFALrCbA.dVzN0UDLzMTN2czW}
```
Stored the output of ```/challenge/run``` command into PWN using _Command Substitution_ to get the flag **pwn.college{g9JEVJYIkKf9m4pjf2WJFALrCbA.dVzN0UDLzMTN2czW}**.

Bash performs the expansion by executing command in a subshell environment and replacing the command substitution with the standard output of the command. Command substitution occurs when a command is enclosed as ```$(command)```

### Reading Input
```
hacker@variables~reading-input:~$ read -p "READ: " PWN
READ: COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{sFO4tCfmuS_n8gPpUm0AA6iIEDA.dhzN1QDLzMTN2czW}
```
Used the ```read``` command to read the value of PWN as COLLEGE, -p argument for the prompt "READ: " to make it clear an input is required, and got the flag **pwn.college{sFO4tCfmuS_n8gPpUm0AA6iIEDA.dhzN1QDLzMTN2czW}**.

### Reading Files
```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{sYa-VB3Q47QhaAvreimwasOaDW5.dBjM4QDLzMTN2czW}
```
The output of ```/challenge/read_me``` command is redirected into/read as the input for PWN in one line to get the flag **pwn.college{sYa-VB3Q47QhaAvreimwasOaDW5.dBjM4QDLzMTN2czW}**.
___