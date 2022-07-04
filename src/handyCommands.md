---
title: 30 Useful Linux Commands for System Administrators
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>

In this article we are going to review some of the useful and frequently used Linux or Unix commands for Linux System Administrators that are used in their daily life.

This is not complete but it’s a compact list of commands to refer to when needed. Let us start one by one how we can use those commands with examples.

## 1. Uptime Command
In Linux uptime command shows how long your system is running and the number of users who are currently logged in and also displays the load average of a system for 1, 5, and 15 minutes intervals.

```sh
uptime
```

```sh
Check Uptime Version
```

Uptime command don’t have other options other than uptime and version. It gives information only in hours:mins:sec if it is less than 1 day.

```sh
uptime -V
```

procps version 3.2.8

## 2. W Command
The w command will display users currently logged in and their process along with showing load averages, login name, tty name, remote host, login time, idle time, JCPU, PCPU, command, and processes.

```sh
w


08:27:44 up 34 min,  1 user,  load average: 0.00, 0.00, 0.08
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
tecmint  pts/0    192.168.50.1     07:59    0.00s  0.29s  0.09s w
```

### Available Options

```sh
-h : displays no header entries.
-s : without JCPU and PCPU.
-f : Removes from the field.
-V : (upper letter) – Shows versions.
```

## 3. Users Command

Users command displays currently logged-in users. This command doesn’t have other parameters other than help and version.

```sh
users
```

## 4. Who Command

who command simply returns the user name, date, time, and host information. who command is similar to w command. Unlike the w command who doesn’t print what users are doing. Let’s illustrate and see the difference between who and w commands.

```
# who

tecmint  pts/0        2012-09-18 07:59 (192.168.50.1)
# w

08:43:58 up 50 min,  1 user,  load average: 0.64, 0.18, 0.06
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
tecmint  pts/0    192.168.50.1     07:59    0.00s  0.43s  0.10s w
Who command Options
-b: Displays last system reboot date and time.
-r: Shows current runlet.
-a, –all: Displays all information cumulatively.
5. Whoami Command
In Linux, a whoami command is used to print the currently logged-in username into your Linux system. If you are logged in as a root using sudo command “whoami” command return root as the current user.

# whoami
```

## 6. ls Command

ls command displays a list of files in a human-readable format.

```sh
ls -l

total 114
dr-xr-xr-x.   2 root root  4096 Sep 18 08:46 bin
dr-xr-xr-x.   5 root root  1024 Sep  8 15:49 boot
Sort file as per last modified time.

# ls -ltr

total 40
-rw-r--r--. 1 root root  6546 Sep 17 18:42 install.log.syslog
-rw-r--r--. 1 root root 22435 Sep 17 18:45 install.log
-rw-------. 1 root root  1003 Sep 17 18:45 anaconda-ks.cfg
```

For more examples of the ls command, please check out our articles:

10 lsof Command Examples in Linux

7 Quirky `ls` Command Tricks Every Linux User Should Know
How to Sort Output of `ls` Command By Last Modified Date and Time


## Crontab Command

List schedule jobs for current user with crontab command and -l option.

```sh
crontab -l


00 10 * * * /bin/ls >/ls.txt
```

Edit your crontab with -e the option. In the below example will open schedule jobs in VI editor. Make necessary changes and quit pressing :wq keys that save the setting automatically.

```sh
crontab -e
```

## Less Command

less command allows quickly viewing the file. You can page up and down. Press ‘q‘ to quit from less window.

```sh
less install.log

Installing setup-2.8.14-10.el6.noarch
warning: setup-2.8.14-10.el6.noarch: Header V3 RSA/SHA256 Signature, key ID c105b9de: NOKEY
Installing filesystem-2.4.30-2.1.el6.i686
Installing ca-certificates-2010.63-3.el6.noarch
Installing xml-common-0.6.3-32.el6.noarch
Installing tzdata-2010l-1.el6.noarch
Installing iso-codes-3.16-2.el6.noarch
```

## More Command

more command allows quickly view file and shows details in percentage. You can page up and down. Press ‘q‘ to quit out from more window.

```sh
more install.log


Installing setup-2.8.14-10.el6.noarch
warning: setup-2.8.14-10.el6.noarch: Header V3 RSA/SHA256 Signature, key ID c105b9de: NOKEY
Installing filesystem-2.4.30-2.1.el6.i686
Installing ca-certificates-2010.63-3.el6.noarch
Installing xml-common-0.6.3-32.el6.noarch
Installing tzdata-2010l-1.el6.noarch
Installing iso-codes-3.16-2.el6.noarch
--More--(10%)
[ You might also like: Learn Why ‘less’ is Faster Than ‘more’ Command for Effective File Navigation ]
```

## CP Command

A `cp` command copies file from source to destination preserving the same mode.

```sh
cp -p fileA fileB
```

You will be prompted before overwriting to file.

```sh
cp -i fileA fileB
```

[ You might also like: How to Force cp Command to Overwrite without Confirmation ]

```sh
MV Command
```

An mv command renames fileA to fileB using the -i option, which prompts confirmation before overwriting. Ask for confirmation if exist already.

```sh
mv -i fileA fileB
```

## Cat Command

The cat command is used to view multiple files at the same time.

```sh
cat fileA fileB
```

You combine more and less command with cat command to view file contain if that doesn’t fit in single screen/page.

```sh
cat install.log | less

cat install.log | more
```

For more examples of Linux, cat commands read our article on 13 Basic Cat Command Examples in Linux.


## cd command (change directory)

with the cd command (change directory or switch directory) it will go to fileA directory.

```sh
cd /fileA
```

```sh
pwd command (print working directory)
```

A pwd command return with the present working directory.

```sh
pwd

/root
```

## Sort command

The sort command is used to sort lines of text files in ascending order. with -r options will sort in descending order.

```sh
sort fileA.txt

# sort -r fileA.txt
```

## VI Command

Vi is the most popular text editor available in most UNIX-like OS. Below examples open file in read-only with -R option. Press ‘:q‘ to quit from vi windows.

```sh
vi -R /etc/shadows
```

## SSH Command (Secure Shell)

SSH command is used to login into the remote host. For example, the below ssh command will connect to the remote host (192.168.50.2) using the user as Narad.

```sh
ssh narad@192.168.50.2
```

To check the version of ssh use the option -V (uppercase) shows version of ssh.

```sh
ssh -V
```

## Ftp or sftp Command

ftp or sftp command is used to connect to remote ftp host. ftp is (file transfer protocol) and sftp is (secure file transfer protocol). For example, the below commands will connect to ftp host (192.168.50.2).

```sh
ftp 192.168.50.2

sftp 192.168.50.2
```

Putting multiple files in remote host with mput similarly, we can do mget to download multiple files from the remote host.

```sh
ftp > mput *.txt

ftp > mget *.txt
```

## Systemctl Command

Systemctl command is a systemd management tool that is used to manage services, check running statuses, start and enable services and work with the configuration files.

```sh
systemctl start httpd.service
systemctl enable httpd.service
systemctl status httpd.service
```

## Free command

The free command shows free, total, and swap memory information in bytes.

```sh
free
             total       used       free     shared    buffers     cached
Mem:       1030800     735944     294856          0      51648     547696
-/+ buffers/cache:     136600     894200
Swap:      2064376          0    2064376
Free with -t options show total memory used and available to use in bytes.

# free -t
             total       used       free     shared    buffers     cached
Mem:       1030800     736096     294704          0      51720     547704
-/+ buffers/cache:     136672     894128
Swap:      2064376          0    2064376
Total:     3095176     736096    2359080
```

## Top Command

top command displays processor activity of your system and also displays tasks managed by kernel in real-time. It’ll show processor and memory are being used.

Using the top command with u the option will display specific User process details as shown below. Press ‘O‘ (uppercase letter) to sort as desired by you. Press ‘q‘ to quit from the top screen.

```sh
top -u tecmint

top - 11:13:11 up  3:19,  2 users,  load average: 0.00, 0.00, 0.00
Tasks: 116 total,   1 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.3%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1030800k total,   736188k used,   294612k free,    51760k buffers
Swap:  2064376k total,        0k used,  2064376k free,   547704k cached

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
1889 tecmint   20   0 11468 1648  920 S  0.0  0.2   0:00.59 sshd
1890 tecmint   20   0  5124 1668 1416 S  0.0  0.2   0:00.44 bash
6698 tecmint   20   0 11600 1668  924 S  0.0  0.2   0:01.19 sshd
6699 tecmint   20   0  5124 1596 1352 S  0.0  0.2   0:00.11 bash
```

For more about top command, we’ve already compiled a list of 12 TOP Command Examples in Linux.

## Tar Command

The tar command is used to compress files and folders in Linux. For example, the below command will create an archive for /home directory with the file name archive-name.tar.

```sh
tar -cvf archive-name.tar /home
```

To extract the tar archive file use the option as follows.

```sh
tar -xvf archive-name.tar
```

## Grep Command

grep command search for a given string in a file. Only tecmint user displays from /etc/passwd file. we can use -i an option for ignoring case sensitivity.

```sh
grep root /etc/passwd

tecmint:x:500:500::/home/tecmint:/bin/bash
```

```sh
Find Command
```

Find command used to search files, strings, and directories. The below example of find command search tecmint word in `/` partition and return the output.

```sh
find / -name root

/var/spool/mail/root
/home/root
/root/home/root
```

## lsof Command

lsof mean List of all open files. Below lsof a command list of all opened files by user tecmint.

```sh
lsof -u root
```

```sh
COMMAND  PID    USER   FD   TYPE     DEVICE SIZE/OFF   NODE NAME
sshd    1889 tecmint  cwd    DIR      253,0     4096      2 /
sshd    1889 tecmint  txt    REG      253,0   532336 298069 /usr/sbin/sshd
sshd    1889 tecmint  DEL    REG      253,0          412940 /lib/libcom_err.so.2.1
sshd    1889 tecmint  DEL    REG      253,0          393156 /lib/ld-2.12.so
sshd    1889 tecmint  DEL    REG      253,0          298643 /usr/lib/libcrypto.so.1.0.0
sshd    1889 tecmint  DEL    REG      253,0          393173 /lib/libnsl-2.12.so
sshd    1889 tecmint  DEL    REG      253,0          412937 /lib/libkrb5support.so.0.1
sshd    1889 tecmint  DEL    REG      253,0          412961 /lib/libplc4.so
```

## last command

With the last command, we can watch the user’s activity in the system. This command can execute normal users also. It will display complete user’s info like terminal, time, date, system reboot or boot, and kernel version. A useful command to troubleshoot.

```sh
last


tecmint  pts/1        192.168.50.1     Tue Sep 18 08:50   still logged in
tecmint  pts/0        192.168.50.1     Tue Sep 18 07:59   still logged in
reboot   system boot  2.6.32-279.el6.i Tue Sep 18 07:54 - 11:38  (03:43)
root     pts/1        192.168.50.1     Sun Sep 16 10:40 - down   (03:53)
root     pts/0        :0.0             Sun Sep 16 10:36 - 13:09  (02:32)
root     tty1         :0               Sun Sep 16 10:07 - down   (04:26)
reboot   system boot  2.6.32-279.el6.i Sun Sep 16 09:57 - 14:33  (04:35)
narad    pts/2        192.168.50.1     Thu Sep 13 08:07 - down   (01:15)
```

You can use last with username to know for specific user’s activity as shown below.

```sh
last tecmint

tecmint  pts/1        192.168.50.1     Tue Sep 18 08:50   still logged in
tecmint  pts/0        192.168.50.1     Tue Sep 18 07:59   still logged in
tecmint  pts/1        192.168.50.1     Thu Sep 13 08:07 - down   (01:15)
tecmint  pts/4        192.168.50.1     Wed Sep 12 10:12 - 12:29  (02:17)
```

## ps command

The ps command displays processes running in the system. The below example show the init to process only.

```sh
ps -ef | grep init

root         1     0  0 07:53 ?        00:00:04 /sbin/init
root      7508  6825  0 11:48 pts/1    00:00:00 grep init
```

### kill command

Use the kill command to terminate the process. First, find process id with ps command as shown below and kill the process with kill -9 command.

```sh
ps -ef | grep init
root         1     0  0 07:53 ?        00:00:04 /sbin/init
root      7508  6825  0 11:48 pts/1    00:00:00 grep init

kill- 9 7508
```

## rm command

rm command used to remove or delete a file without prompting for confirmation.

```sh
rm filename
```

Use the `-i` option to get confirmation before removing it. Using optons `-r` and `-f` will remove the file forcefully without confirmation.

```sh
rm -i test.txt
```

rm: remove regular file `test.txt'?


```sh
mkdir command example.
```

mkdir command is used to create directories under Linux.

```sh
mkdir directoryname
```

This is a handy day-to-day used basic commands in Linux / Unix-like operating system. Kindly share through our comment box if we missed out.

## sed `for text read and write to files`

It often happens that I want to add text to a file, for instace I want to have some page stats on my blog. At the moment I am using a static site generator. The one I'm using can't auto add a `script` tag to each page, so I have to go add it manually to each page. This

It the moment I have some `yml` at the top of each page that  looks like this:

```md
---
title: Page title goes here
```

I want to update that so that is looks like:

```md
---
title: Page title goes here
---
<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>
```

So, to do that I will use the `find` command with `sed` command:

This will find all files with extensions `.md` in the current `folder` and `sub-folders`. Then it will find the line containing `title\: ` (have to add `\` before `:` to escape the `:` that has some function) Then it will append a new line with `/&` Then I will add  `---` and add another line with `/&` to close the `yml` part of the document. Then finally add `<script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script>` and add another line with `/&`


```sh
find ./*.md -type f -exec sed -i -e 's/title\:/& ---/& <script type="text/javascript">(function(w,s){var e=document.createElement("script");e.type="text/javascript";e.async=true;e.src="https://cdn.pagesense.io/js/webally/f2527eebee974243853bcd47b32631f4.js";var x=document.getElementsByTagName("script")[0];x.parentNode.insertBefore(e,x);})(window,"script");</script> /&
```

That did work :)

