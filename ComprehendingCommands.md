# Comprehending Commands

### cat: not the pet, but the command!
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{oOXhFrDmFIGlknFLfWUk3YKbnyC.dFzN1QDLzMTN2czW}
```
Used ```cat``` to read the ```flag``` file. Got the flag **pwn.college{oOXhFrDmFIGlknFLfWUk3YKbnyC.dFzN1QDLzMTN2czW}**.

### catting absolute paths
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{cRnTuGQqW_nLdL30nuGyE9MJk4x.dlTM5QDLzMTN2czW}
```
Used ```cat``` to read the ```/flag``` file. Got the flag **pwn.college{cRnTuGQqW_nLdL30nuGyE9MJk4x.dlTM5QDLzMTN2czW}**.

### more catting practice

```
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/include/gap/flag. Go cat it out **without** cding into that 
directory!
hacker@commands~more-catting-practice:~$ cat /usr/include/gap/flag
pwn.college{0m2Bhg_nELpSAvUdUiQuqOD8uWo.dBjM5QDLzMTN2czW}
```
Used ```cat``` to read the ```/usr/include/gap/flag``` file. Got the flag **pwn.college{0m2Bhg_nELpSAvUdUiQuqOD8uWo.dBjM5QDLzMTN2czW}**.

### grepping for a needle in a haystack
```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{spGEIpLI3KuJSgyb3jEbME6H1K4.ddTM4QDLzMTN2czW}
```
Used ```grep```command to find "pwn.college" string in ```/challenge/data.txt``` to get the flag **pwn.college{spGEIpLI3KuJSgyb3jEbME6H1K4.ddTM4QDLzMTN2czW}**.

### listing files
```
hacker@commands~listing-files:~$ ls /challenge
19592-renamed-run-8069  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/19592-renamed-run-8069  
Yahaha, you found me! Here is your flag:
pwn.college{cb41mfECY7KEyrys2mxoRKjlMuy.dhjM4QDLzMTN2czW}
```
Used ```ls```command to find run file's name in ```/challenge``` directory and then invoked ```/challenge/19592-renamed-run-8069``` to get the flag **pwn.college{cb41mfECY7KEyrys2mxoRKjlMuy.dhjM4QDLzMTN2czW}**.

### touching files
```
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{sllOAaADiv9eGGg8WBRiTh4-lhz.dBzM4QDLzMTN2czW}
```
Used ```touch```command to create files ```/tmp/pwn``` and ```/tmp/college``` and then invoked ```/challenge/run``` to get the flag **pwn.college{sllOAaADiv9eGGg8WBRiTh4-lhz.dBzM4QDLzMTN2czW}**.

### removing files
```
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{kiQeghmAs4Km5CrzGL9XAU8curM.dZTOwUDLzMTN2czW}
```
Used ```rm```command to delete file ```delete_me``` and then invoked ```/challenge/check``` to get the flag **pwn.college{kiQeghmAs4Km5CrzGL9XAU8curM.dZTOwUDLzMTN2czW}**.

### hidden files
```
hacker@commands~hidden-files:~$ ls / -a
.   .dockerenv            bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-70062082310007  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat /.flag-70062082310007
pwn.college{ElPqhLlwIW-2Z3O00qHxVm3zeQ9.dBTN4QDLzMTN2czW}
```
Used ```ls -a```command to list all files, including hidden ones,then used ```cat /.flag-70062082310007``` to read the flag **pwn.college{ElPqhLlwIW-2Z3O00qHxVm3zeQ9.dBTN4QDLzMTN2czW}**.

### An Epic Filesystem Quest
```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
MESSAGE  bin  boot  challenge  dev  etc  flag  home  lib  lib32  lib64  libx32  media  mnt  nix  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
hacker@commands~an-epic-filesystem-quest:/$ cat MESSAGE
Congratulations, you found the clue!
The next clue is in: /opt/angr-management/_internal/archr/implants

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/angr-management/_internal/archr/implants
hacker@commands~an-epic-filesystem-quest:/opt/angr-management/_internal/archr/implants$ ls
EVIDENCE  GENERIC  __init__.py  __pycache__  bintrace_qemu  emurrate  gdb  gdbserver  ltrace  qtrace  rr  shellphish_qemu  udp_tcp_convert
hacker@commands~an-epic-filesystem-quest:/opt/angr-management/_internal/archr/implants$ cat EVIDENCE
Tubular find!
The next clue is in: /usr/share/perl5/Dpkg/Source
hacker@commands~an-epic-filesystem-quest:/opt/angr-management/_internal/archr/implants$ cd /usr/share/perl5/Dpkg/Source
hacker@commands~an-epic-filesystem-quest:/usr/share/perl5/Dpkg/Source$ ls
Archive.pm  BinaryFiles.pm  CLUE  Format.pm  Functions.pm  Package  Package.pm  Patch.pm  Quilt.pm
hacker@commands~an-epic-filesystem-quest:/usr/share/perl5/Dpkg/Source$ cat CLUE
Yahaha, you found me!
The next clue is in: /usr/share/doc/libopus0

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/share/perl5/Dpkg/Source$ cd /usr/share/doc/libopus0
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libopus0$ ls
INFO  changelog.Debian.gz  copyright
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libopus0$ cat INFO
Great sleuthing!
The next clue is in: /usr/lib/x86_64-linux-gnu/perl/5.30.0/auto/Hash/Util

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libopus0$ ls /usr/lib/x86_64-linux-gnu/perl/5.30.0/auto/Hash/Util
FieldHash  Util.so  WHISPER-TRAPPED
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libopus0$ cat /usr/lib/x86_64-linux-gnu/perl/5.30.0/auto/Hash/Util/WHISPER-TRAPPED
Congratulations, you found the clue!
The next clue is in: /usr/share/doc/eclib-tools

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/libopus0$ cd /usr/share/doc/eclib-tools
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/eclib-tools$ ls -a
.  ..  .NUGGET  changelog.Debian.gz  copyright
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/eclib-tools$ cat .NUGGET
Great sleuthing!
The next clue is in: /opt/linux/linux-5.4/include/generated/uapi
hacker@commands~an-epic-filesystem-quest:/usr/share/doc/eclib-tools$ cd /opt/linux/linux-5.4/include/generated/uapi
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/generated/uapi$ ls
TEASER  linux
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/generated/uapi$ cat TEASER
Congratulations, you found the clue!
The next clue is in: /opt/angr-management/_internal/pypcode/processors/HCS08/data/languages
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/include/generated/uapi$ cd /opt/angr-management/_internal/pypcode/processors/HCS08/data/languages
hacker@commands~an-epic-filesystem-quest:/opt/angr-management/_internal/pypcode/processors/HCS08/data/languages$ ls
HC05-M68HC05TB.pspec  HC05.ldefs  HC05.sla      HC08-MC68HC908QY4.pspec  HC08.pspec  HC08.slaspec            HCS08.cspec  HCS08.opinion  HCS08.sla      HCS_HC.sinc
HC05.cspec            HC05.pspec  HC05.slaspec  HC08.ldefs               HC08.sla    HCS08-MC9S08GB60.pspec  HCS08.ldefs  HCS08.pspec    HCS08.slaspec  MEMO
hacker@commands~an-epic-filesystem-quest:/opt/angr-management/_internal/pypcode/processors/HCS08/data/languages$ cat MEMO
Tubular find!
The next clue is in: /opt/busybox/busybox-1.33.2/include/config/feature/ftpd

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/opt/angr-management/_internal/pypcode/processors/HCS08/data/languages$ cd /opt/busybox/busybox-1.33.2/include/config/feature/ftpd
hacker@commands~an-epic-filesystem-quest:/opt/busybox/busybox-1.33.2/include/config/feature/ftpd$ ls
POINTER  accept  authentication.h  write.h
hacker@commands~an-epic-filesystem-quest:/opt/busybox/busybox-1.33.2/include/config/feature/ftpd$ cat POINTER
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{owzWOrUw4R25h-8T0pGEFpoYTkE.dljM4QDLzMTN2czW}
```
Used ```cd```, ```cat``` and ```ls``` commands as per the clues to finally get the flag **pwn.college{owzWOrUw4R25h-8T0pGEFpoYTkE.dljM4QDLzMTN2czW}**.

### making directories
```
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{QnCvmjiORf75kKO9dNQrArxy_Dl.dFzM4QDLzMTN2czW}
```
Used ```mkdir``` to create directory ```/tmp/pwn```, then used ```touch``` command to create file ```/tmp/pwn/college``` and finally invoked ```/challenge/run``` to get the flag **pwn.college{QnCvmjiORf75kKO9dNQrArxy_Dl.dFzM4QDLzMTN2czW}**.

### finding files
```
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/tmp/tmp.G9qthVCks5’: Permission denied
/usr/local/share/radare2/5.9.5/flag
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
find: ‘/home/hacker/lost+found’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
find: ‘/var/cache/private’: Permission denied
find: ‘/var/log/private’: Permission denied
find: ‘/var/log/apache2’: Permission denied
find: ‘/var/log/mysql’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/mysql-keyring’: Permission denied
find: ‘/var/lib/php/sessions’: Permission denied
find: ‘/var/lib/private’: Permission denied
find: ‘/var/lib/mysql-files’: Permission denied
find: ‘/var/lib/mysql’: Permission denied
find: ‘/run/mysqld’: Permission denied
find: ‘/run/sudo’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/1/task/1/fd’: Permission denied
find: ‘/proc/1/task/1/fdinfo’: Permission denied
find: ‘/proc/1/task/1/ns’: Permission denied
find: ‘/proc/1/fd’: Permission denied
find: ‘/proc/1/map_files’: Permission denied
find: ‘/proc/1/fdinfo’: Permission denied
find: ‘/proc/1/ns’: Permission denied
find: ‘/proc/7/task/7/fd’: Permission denied
find: ‘/proc/7/task/7/fdinfo’: Permission denied
find: ‘/proc/7/task/7/ns’: Permission denied
find: ‘/proc/7/fd’: Permission denied
find: ‘/proc/7/map_files’: Permission denied
find: ‘/proc/7/fdinfo’: Permission denied
find: ‘/proc/7/ns’: Permission denied
/opt/aflplusplus/nyx_mode/QEMU-Nyx/nbd/flag
/opt/pwndbg/.venv/lib/python3.8/site-packages/pwnlib/flag
/opt/radare2/libr/flag
/nix/store/pmvk2bk4p550w182rjfm529kfqddnvh3-python3.11-pwntools-4.12.0/lib/python3.11/site-packages/pwnlib/flag
/nix/store/1yagn5s8sf7kcs2hkccgf8d0wxlrv5sz-radare2-5.9.0/share/radare2/5.9.0/flag
hacker@commands~finding-files:~$ cat /usr/local/share/radare2/5.9.5/flag
cat: /usr/local/share/radare2/5.9.5/flag: Is a directory
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ cat /opt/aflplusplus/nyx_mode/QEMU-Nyx/nbd/flag
pwn.college{UV5VtVhp9WY6twAv3syrb8GlH1y.dJzM4QDLzMTN2czW}
```
Used ```find``` command to find all the files in the filesystem named flag, then used hit and trial to get the flag **pwn.college{UV5VtVhp9WY6twAv3syrb8GlH1y.dJzM4QDLzMTN2czW}**.

### linking files
```
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{UxQys61xQU5ymAeldwVWSceL4_Q.dlTM1UDLzMTN2czW}
```
Used ```ln -s``` command to make ```home/hacker/not-the-flag``` a symbolic link (or _symlink_) of ```/flag``` then invoked ```/challenge/catflag``` to get the flag **pwn.college{UxQys61xQU5ymAeldwVWSceL4_Q.dlTM1UDLzMTN2czW}**.
___





