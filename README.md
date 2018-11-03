Linux System Administrator/DevOps Interview Questions
====================================================

A collection of linux sysadmin/devops interview questions. Feel free to contribute via pull requests, issues or email messages.


## <a name='toc'>Table of Contents</a>

  1. [Contributors](#contributors)
  1. [General Questions](#general)
  1. [Simple Linux Questions](#simple)
  1. [Medium Linux Questions](#medium)
  1. [Hard Linux Questions](#hard)
  1. [Expert Linux Questions](#expert)
  1. [Networking Questions](#network)
  1. [MySQL Questions](#mysql)
  1. [DevOps Questions](#devop)
  1. [Fun Questions](#fun)
  1. [Demo Time](#demo)
  1. [Other Great References](#references)


#### [[⬆]](#toc) <a name='contributors'>Contributors:</a>

* [moregeek](https://github.com/moregeek)
* [typhonius](https://github.com/typhonius)
* [schumar](https://github.com/schumar)
* [negesti](https://github.com/negesti)
* peter
* [andreashappe](https://github.com/andreashappe)
* [quatrix](https://github.com/quatrix)
* [biyanisuraj](https://github.com/biyanisuraj)
* [pedroguima](https://github.com/pedroguima)
* Ben
* [bharatnc](https://github.com/bharatnc)


#### [[⬆]](#toc) <a name='general'>General Questions:</a>

* What did you learn yesterday/this week?
Birthday Paradox
printf
regex
grep

* Talk about your preferred development/administration environment. (OS, Editor, Browsers, Tools etc.)
Ubuntu 16.04
Pycharm
VScode
Chrome
Vim
Bash

* Tell me about the last major Linux project you finished.
Nginx
Gunicorn
Flask

* Tell me about the biggest mistake you've made in [some recent time period] and how you would do it differently today. What did you learn from this experience?
Terminated the AWS Instance which erased all my website data.
I should do backup more often and turn on the terminate protection.

* Why we must choose you?
Experienced in Python, good at Software dev, interested in Linux and like to solve diffcult bugs.

* What function does DNS play on a network?
Domain Name Servers (DNS) are the Internet's equivalent of a phone book.

* What is HTTP?
HTTP means HyperText Transfer Protocol. HTTP is the underlying protocol used by the World Wide Web and this protocol defines how messages are formatted and transmitted, and what actions Web servers and browsers should take in response to various commands.

* What is an HTTP proxy and how does it work?
HTTP functions as a request–response protocol in the client–server computing model. HTTP is an application layer protocol designed within the framework of the Internet protocol suite. Its definition presumes an underlying and reliable/unreliable transport layer: TCP/UDP.
HTTP resources are identified and located on the network by Uniform Resource Locators (URLs), using the Uniform Resource Identifiers (URI's) schemes http and https. 

how does it work:
  1) An HTTP client initiates a request by establishing a TCP connection to a particular port on a server (typically port 80, occasionally port 8080)
  2) An HTTP server listening on that port waits for a client's request message.
  3) Upon receiving the request, the server sends back a status line, such as "HTTP/1.1 200 OK", and a message of its own.
  
  GET, POST, PUT, DELETE, OPTIONS, HEAD, TRACE, CONNECT, PATCH
  Informational 1XX
  Successful 2XX
  Redirection 3XX
  Client Error 4XX
  Server Error 5XX
  
* Describe briefly how HTTPS works.
HyperText Transfer Protocol Secure. Using HTTPS, the computers agree on a "code" between them, and then they scramble the messages using that "code" so that no one in between can read them. This keeps your information safe from hackers. HTTPS encrypts all message contents, including the HTTP headers and the request/response data.
 
* What is SMTP? Give the basic scenario of how a mail message is delivered via SMTP.
Simple Mail Transfer Protocol (SMTP) is an Internet standard for electronic mail (email) transmission
SMTP is a delivery protocol only. In normal use, mail is "pushed" to a destination mail server. While other protocols, such as the Post Office Protocol (POP) and the Internet Message Access Protocol (IMAP) are specifically designed for use by individual users retrieving messages and managing mail boxes. 
MAIL
RCPT
DATA

* What is RAID? What is RAID0, RAID1, RAID5, RAID10?
RAID (Redundant Array of Independent Disks) data storage virtualization technology that combines multiple physical disk drive components into one or more logical units for the purposes of data redundancy, performance improvement, or both.

  1) RAID0: Multiple disks be striped, No Redundancy, Excellent performance. (striping spreads data across more physical drives, multiple disks can access the contents of a file, enabling writes and reads to be completed more quickly)

  2) RAID1: Mirroring, Redundancy, Bad Performance and waste of space
  
  3) RAID5: minimum 3 disks, Redundancy(Distributed Parity), Cost effective, Heavy Read, write is slow
  
  4) RAID10: minimum 4 disks, Redundancy, Cost a lot

* What is a level 0 backup? What is an incremental backup? 
Incremental backups are successive copies of the data contain only the portion that has changed since the preceding backup copy was made. It's often desirable as they reduce storage space usage, and are quicker to perform than differential backups.

Incremental backups can be either level 0 or level 1. A level 0 incremental backup, which is the base for subsequent incremental backups, copies all blocks containing data, backing the datafile up into a backup set just as a full backup would.

* Describe the general file system hierarchy of a Linux system.
/
/root
/bin
/boot
/dev
/etc
/home
/lib
/var
/usr
/tmp


#### [[⬆]](#toc) <a name='simple'>Simple Linux Questions:</a>

* What is the name and the UID of the administrator user?
root 0
$ id root
uid=0(root) gid=0(root) groups=0(root)

* How to list all files, including hidden ones, in a directory?

ls -a
alias ll = 'ls -alF'

* What is the Unix/Linux command to remove a directory and its contents?

rm -R [folder path] 
You can also add -i to make sure you are deleting right files

* Which command will show you free/used memory? Does free memory exist on Linux?

free -m
free -h
top (realtime)
vmstat -s

Free memory as in unused? Very little. Any memory not used by a program is used to cache disk. It will use all the memory to accelarate the speed of process.

This is just a difference in terminology. Both you and Linux agree that memory taken by applications is "used", while memory that isn't used for anything is "free". But how do you count memory that is currently used for something, but can still be made available to applications? You might count that memory as "free" and/or "available". Linux instead counts it as "used", but also "available".


* How to search for the string "my konfu is the best" in files of a directory recursively?
grep -r 'my konfu is the best' [path]

* How to connect to a remote server or what is SSH?
SSH or Secure Shell is a network communication protocol that enables two computers to communicate. An inherent feature of ssh is that the communication between the two computers is encrypted meaning that it is suitable for use on insecure networks.

ssh remote_username@remote_host


* How to get all environment variables and how can you use them?
export
printenv

* I get "command not found" when I run ```ifconfig -a```. What can be wrong?
```type -a ifconfig```
the command syntax was entered incorrectly
the command you are attempting to run is not installed
the command was deleted, or, worse, the system directory was deleted or modified
the users $PATH is incomplete, or $PATH has been erroneously set, reset, or cleared – this is the most common reason to see a ‘command not found’ message

* What happens if I type TAB-TAB?
suggest all posibilities of the command
TAB will display the files

* What command will show the available disk space on the Unix/Linux system?
df - report file system disk space usage
df -h (human readable unit)

* What commands do you know that can be used to check DNS records?
nslookup
host [address]
ping?

* What Unix/Linux commands will alter a files ownership, files permissions?
chown - command to change file owner and group information.
chmod - command to change file access permissions such as read, write, and access.

* What does ```chmod +x FILENAME``` do?
make the file excutable for owner, group and other groups

* What does the permission 0750 on a file mean?
$ chmod 750 FILENAME
-rwxr-x--- 1 root root 24 Jan 22 18:02 FILENAME*
0111 0101 0000
This permissions means that owner can read\write\execute this file, also members of group can read and execute, other users can do nothing with it.

* What does the permission 0750 on a directory mean?
This permissions means that owner can read\write\execute(see file list of directory) this directory, also members of group can read and list, other users can do nothing with it.

* How to add a new system user without login permissions?


* How to add/remove a group from a user?


* What is a bash alias?
alias is like a shortcur for some commands setup

* How do you set the mail address of the root/a user?
useradd -r subversion
per man useradd:
-r, --system                  create a system account
They will have the shell /usr/sbin/nologin and have logins disabled

* What does CTRL-c do?
Control+Z is used for suspending a process by sending it the signal SIGSTOP, which cannot be intercepted by the program. While Control+C is used to kill a process with the signal SIGINT, and can be intercepted by a program so it can clean its self up before exiting, or not exit at all.
However, if you kill one, you won't see any confirmation other than being dropped back to a shell prompt. When you suspend a process, you can do fancy things with it, too. For instance, running this:
fg
With a program suspended will bring it back to the foreground.
And running the command
bg
With a program suspended will allow it to run in the background (the program's output will still go to the TTY, though).
If you want to kill a suspended program, you don't have to bring it back with fg first, you can simply do the command:
kill %1
If you have multiple suspended commands, running
jobs

* What is in /etc/services?
UNIX uses the /etc/services file as a small local database. For each service this
file specifies the service’s well-known port number and notes whether the service is available as a TCP or
UDP service. The /etc/services file is distributed as part of the UNIX operating system. 


* How to redirect STDOUT and STDERR in bash? (> /dev/null 2>&1)
* What is the difference between UNIX and Linux.
* What is the difference between Telnet and SSH?
* Explain the three load averages and what do they indicate. What command can be used to view the load averages?
* Can you name a lower-case letter that is not a valid option for GNU ```ls```?
* What is a Linux kernel module?
* Walk me through the steps in booting into single user mode to troubleshoot a problem.
* Walk me through the steps you'd take to troubleshoot a 404 error on a web application you administer.

#### [[⬆]](#toc) <a name='medium'>Medium Linux Questions:</a>

* What do the following commands do and how would you use them?
 * ```tee```
 * ```awk```
 * ```tr```
 * ```cut```
 * ```tac```
 * ```curl```
 * ```wget```
 * ```watch```
 * ```head```
 * ```tail```
* What does an ```&``` after a command do?
* What does ```& disown``` after a command do?
* What is a packet filter and how does it work?
* What is Virtual Memory?
* What is swap and what is it used for?
* What is an A record, an NS record, a PTR record, a CNAME record, an MX record?
* Are there any other RRs and what are they used for?
* What is a Split-Horizon DNS?
* What is the sticky bit?
* What does the immutable bit do to a file?
* What is the difference between hardlinks and symlinks? What happens when you remove the source to a symlink/hardlink?
* What is an inode and what fields are stored in an inode?
* How to force/trigger a file system check on next reboot?
* What is SNMP and what is it used for?
* What is a runlevel and how to get the current runlevel?
* What is SSH port forwarding?
* What is the difference between local and remote port forwarding?
* What are the steps to add a user to a system without using useradd/adduser?
* What is MAJOR and MINOR numbers of special files?
* Describe the mknod command and when you'd use it.
* Describe a scenario when you get a "filesystem is full" error, but 'df' shows there is free space.
* Describe a scenario when deleting a file, but 'df' not showing the space being freed.
* Describe how 'ps' works.
* What happens to a child process that dies and has no parent process to wait for it and what’s bad about this?
* Explain briefly each one of the process states.
* How to know which process listens on a specific port?
* What is a zombie process and what could be the cause of it?
* You run a bash script and you want to see its output on your terminal and save it to a file at the same time. How could you do it?
* Explain what echo "1" > /proc/sys/net/ipv4/ip_forward does.
* Describe briefly the steps you need to take in order to create and install a valid certificate for the site https://foo.example.com.
* Can you have several HTTPS virtual hosts sharing the same IP?
* What is a wildcard certificate?
* Which Linux file types do you know?
* What is the difference between a process and a thread? And parent and child processes after a fork system call?
* What is the difference between exec and fork?
* What is "nohup" used for?
* What is the difference between these two commands?
 * ```myvar=hello```
 * ```export myvar=hello```
* How many NTP servers would you configure in your local ntp.conf?
* What does the column 'reach' mean in ```ntpq -p``` output?
* You need to upgrade kernel at 100-1000 servers, how you would do this?
* How can you get Host, Channel, ID, LUN of SCSI disk?
* How can you limit process memory usage?
* What is bash quick substitution/caret replace(^x^y)?
* Do you know of any alternative shells? If so, have you used any?
* What is a tarpipe (or, how would you go about copying everything, including hardlinks and special files, from one server to another)?
* How can you tell if the httpd package was already installed?
* How can you list the contents of a package?
* How can you determine which package is better: openssh-server-5.3p1-118.1.el6_8.x86_64 or openssh-server-6.6p1-1.el6.x86_64 ?
* Can you explain to me the difference between block based, and object based storage?

#### [[⬆]](#toc) <a name='hard'>Hard Linux Questions:</a>

* What is a tunnel and how you can bypass a http proxy?
* What is the difference between IDS and IPS?
* What shortcuts do you use on a regular basis?
* What is the Linux Standard Base?
* What is an atomic operation?
* Your freshly configured http server is not running after a restart, what can you do?
* What kind of keys are in ~/.ssh/authorized_keys and what it is this file used for?
* I've added my public ssh key into authorized_keys but I'm still getting a password prompt, what can be wrong?
* Did you ever create RPM's, DEB's or solaris pkg's?
* What does ```:(){ :|:& };:``` do on your system?
* How do you catch a Linux signal on a script?
* Can you catch a SIGKILL?
* What's happening when the Linux kernel is starting the OOM killer and how does it choose which process to kill first?
* Describe the linux boot process with as much detail as possible, starting from when the system is powered on and ending when you get a prompt.
* What's a chroot jail?
* When trying to umount a directory it says it's busy, how to find out which PID holds the directory?
* What's LD_PRELOAD and when it's used?
* You ran a binary and nothing happened. How would you debug this?
* What are cgroups? Can you specify a scenario where you could use them?
* How can you remove/delete a file with file-name consisting of only non-printable/non-type-able characters?
* How can you increase or decrease the priority of a process in Linux?
* What are run-levels in Linux?


#### [[⬆]](#toc) <a name='expert'>Expert Linux Questions:</a>

* A running process gets ```EAGAIN: Resource temporarily unavailable``` on reading a socket. How can you close this bad socket/file descriptor without killing the process?
* What do you control with swapiness?
* How do you change TCP stack buffers? How do you calculate it?
* What is Huge Tables? Why isn't it enabled by default? Why and when use it?
* What is LUKS? How to use it?


#### [[⬆]](#toc) <a name='network'>Networking Questions:</a>

* What is localhost and why would ```ping localhost``` fail?
* What is the similarity between "ping" & "traceroute" ? How is traceroute able to find the hops.
* What is the command used to show all open ports and/or socket connections on a machine?
* Is 300.168.0.123 a valid IPv4 address?
* Which IP ranges/subnets are "private" or "non-routable" (RFC 1918)?
* What is a VLAN?
* What is ARP and what is it used for?
* What is the difference between TCP and UDP?
* What is the purpose of a default gateway?
* What is command used to show the routing table on a Linux box?
* A TCP connection on a network can be uniquely defined by 4 things. What are those things?
* When a client running a web browser connects to a web server, what is the source port and what is the destination port of the connection?
* How do you add an IPv6 address to a specific interface?
* You have added an IPv4 and IPv6 address to interface eth0. A ping to the v4 address is working but a ping to the v6 address gives you the response ```sendmsg: operation not permitted```. What could be wrong?
* What is SNAT and when should it be used?
* Explain how could you ssh login into a Linux system that DROPs all new incoming packets using a SSH tunnel.
* How do you stop a DDoS attack?
* How can you see content of an ip packet?
* What is IPoAC (RFC 1149)?
* What will happen when you bind port 0?



#### [[⬆]](#toc) <a name='mysql'>MySQL questions:</a>

* How do you create a user?
* How do you provide privileges to a user?
* What is the difference between a "left" and a "right" join?
* Explain briefly the differences between InnoDB and MyISAM.
* Describe briefly the steps you need to follow in order to create a simple master/slave cluster.
* Why should you run "mysql_secure_installation" after installing MySQL?
* How do you check which jobs are running?
* How would you take a backup of a MySQL database?

#### [[⬆]](#toc) <a name='devop'>DevOps Questions:</a>

* Can you describe your workflow when you create a script?
* What is GIT?
* What is a dynamically/statically linked file?
* What does "./configure && make && make install" do?
* What is puppet/chef/ansible used for?
* What is Nagios/Zenoss/NewRelic used for?
* What is Jenkins/TeamCity/GoCI used for?
* What is the difference between Containers and VMs?
* How do you create a new postgres user?
* What is a virtual IP address? What is a cluster?
* How do you print all strings of printable characters present in a file?
* How do you find shared library dependencies?
* What is Automake and Autoconf?
* ./configure shows an error that libfoobar is missing on your system, how could you fix this, what could be wrong?
* What are the advantages/disadvantages of script vs compiled program?
* What's the relationship between continuous delivery and DevOps?
* What are the important aspects of a system of continuous integration and deployment?
* How would you enable network file sharing within AWS that would allow EC2 instances in multiple availability zones to share data?

#### [[⬆]](#toc) <a name='fun'>Fun Questions:</a>

* A careless sysadmin executes the following command: ```chmod 444 /bin/chmod ``` - what do you do to fix this?
* I've lost my root password, what can I do?
* I've rebooted a remote server but after 10 minutes I'm still not able to ssh into it, what can be wrong?
* If you were stuck on a desert island with only 5 command-line utilities, which would you choose?
* You come across a random computer and it appears to be a command console for the universe. What is the first thing you type?
* Tell me about a creative way that you've used SSH?
* You have deleted by error a running script, what could you do to restore it?
* What will happen on 19 January 2038?
* How to reboot server when reboot command is not responding?


#### [[⬆]](#toc) <a name='demo'>Demo Time:</a>

* Unpack test.tar.gz without man pages or google.
* Remove all "*.pyc" files from testdir recursively?
* Search for "my konfu is the best" in all *.py files.
* Replace the occurrence of "my konfu is the best" with "I'm a linux jedi master" in all *.txt files.
* Test if port 443 on a machine with IP address X.X.X.X is reachable.
* Get http://myinternal.webserver.local/test.html via telnet.
* How to send an email without a mail client, just on the command line?
* Write a ```get_prim``` method in python/perl/bash/pseudo.
* Find all files which have been accessed within the last 30 days.
* Explain the following command ```(date ; ps -ef | awk '{print $1}' | sort | uniq | wc -l ) >> Activity.log```
* Write a script to list all the differences between two directories.
* In a log file with contents as ```<TIME> : [MESSAGE] : [ERROR_NO] - Human readable text``` display summary/count of specific error numbers that occurred every hour or a specific hour.


#### [[⬆]](#toc) <a name='references'>Other Great References:</a>

Some questions are 'borrowed' from other great references like:

* https://github.com/darcyclarke/Front-end-Developer-Interview-Questions
* https://github.com/kylejohnson/linux-sysadmin-interview-questions/blob/master/test.md
* http://slideshare.net/kavyasri790693/linux-admin-interview-questions
