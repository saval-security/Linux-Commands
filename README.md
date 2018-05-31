# Linux Command Line Cheatsheet
Basic Linux Commands.

A curated list of commonly used linux commands, easily accessible in one location. I have used linux fairly often and am pretty comfortable using most of these commands. However I sometimes forget syntax/options for a particular command, and need to look it up. While most guides I've found under [resources](#resources) provide a lot of great information, the guides always seemed random in nature. I created this guide to attempt to help make some commands easier to read and find, and how they are commonly used (or at least how I've commonly used them). 

**_This is not the end all - be all guide for linux commands. Just some basic/intermediate commands, with some options for how to commonly use them._**

---

## Table of Contents

- [File and Directory Commands](#file-and-directory-commands)
  - [File Administration](#file-administration)
    - [Basic Commands](#fa-basic)
    - [Intermediate Commands](#fa-inter)
    - [Examples](#fa-ex) 
  - [File Systems](#file-systems)
    - [Basic Commands](#fs-basic)
    - [Intermediate Commands](#fs-inter)
    - [Examples](#fs-ex)
- [System Commands](#system-commands)
  - [System](#system)
    - [Basic Commands](#s-basic)
    - [Intermediate Commands](#s-inter)
    - [Examples](#s-ex)
  - [Networking](#networking)
    - [Basic Commands](#net-basic)
    - [Intermediate Commands](#net-inter)
    - [Examples](#net-ex)
- [Other](#other)
  - [Random](#random)
  - [Shortcuts](#shortcuts)
- [Resources](#resources)
  
---

## File and Directory Commands
**_Some commands for file and directory administration in Linux_**


### File Administration

<a id="fa-basic"></a>

| Basic Commands | Description | Man Page | Example |
| --- | --- | --- | --- |
| **`cat`** | Displays contents of a file. | [Link](http://man7.org/linux/man-pages/man1/cat.1.html) | [Jump to Example](#cat-anc) |
| **`less`** | Used to browse contents of a file. | [Link](http://man7.org/linux/man-pages/man1/less.1.html) | [Jump to Example](#less-anc) |
| **`touch`** | Creates empty file. | [Link](http://man7.org/linux/man-pages/man1/touch.1.html) | [Jump to Example](#touch-anc) |
| **`file`** | Determines and prints out file type | [Link](http://man7.org/linux/man-pages/man1/file.1.html) | [Jump to Example](#file-anc) |
| **`cp`** | Copy files through command line. Can also copy full directories. | [Link](http://man7.org/linux/man-pages/man1/cp.1.html) | [Jump to Example](#cp-anc) |
| **`mv`** | Moves file to a different location. Also used for renaming files. | [Link](http://man7.org/linux/man-pages/man1/mv.1.html) | [Jump to Example](#mv-anc) |
| **`rm`** | Removes file. Can also be used to remove entire directories. | [Link](http://man7.org/linux/man-pages/man1/rm.1.html) | [Jump to Example](#rm-anc) |
| **`echo`** | Dsiplays a line of text. Typically used to add text to a file. | [Link](http://man7.org/linux/man-pages/man1/echo.1.html) | [Jump to Example](#echo-anc) |
| **`nano`** & **`vi`** | Text editors built into linux command line. | none | [Jump to Example](#nano-anc) |

<a id="fa-inter"></a>

| Intermediate Commands | Description | Man Page | Example |
| --- | --- | --- | --- |
| **`ln`** | Creates links between files. Hard links refer to the target file linking to the data on the disk of the source file. Soft links refer to the target file linking to the source file, which then links to the data on the disk. Hard link = Tfile -> data <- Sfile. Soft link = Tfile -> Sfile -> data. | [Link](http://man7.org/linux/man-pages/man1/ln.1.html) | [Jump to Example](#ln-anc) |
| **`chmod`** | Changes file mode bits to allow for setting file permissions. | [Link](http://man7.org/linux/man-pages/man1/chmod.1.html) | [Jump to Example](#chmod-anc) |
| **`chown`** | Change file owner and group | [Link](http://man7.org/linux/man-pages/man1/chown.1.html) | [Jump to Example](#chown-anc) |
| **`gzip`** | Compresses contents of files. | [Link]() | [Jump to Example](#gzip-anc) |
| **`tar`** | Archives file(s) (Compression is optional). | [Link](http://man7.org/linux/man-pages/man1/tar.1.html) | [Jump to Example](#tar-anc) |
| **`zip`** | | [Link]() | [Jump to Example](#zip-anc) |
| **`unzip`** | | [Link]() | [Jump to Example](#unzip-anc) |
| **`diff`** | Compares the content of two files. Output is all lines that do not match. | [Link](http://man7.org/linux/man-pages/man1/diff.1.html) | [Jump to Example](#diff-anc) |

<a id="fa-ex"></a>

#### Examples 

|<a id="cat-anc"></a> Command | Common Options |
| --- | --- |
| **`cat filename`** | Commonly used without any options |
```bash
cat secrets.txt               #prints contents of secrets.txt
```

|<a id="less-anc"></a> Command | Common Options |
| --- | --- |
| **`less filename`** | Commonly used without any options  |
```bash
less secrets.txt              #Displays contents of secrets.txt. Good to use for bigger files for easier navigation of content
```

|<a id="touch-anc"></a> Command | Common Options |
| --- | --- |
| **`touch filename`** | Commonly used without any options |
```bash
touch new_screts.txt          #creates empty txt file called new_secrets.txt
```

|<a id="file-anc"></a> Command | Common Options |
| --- | --- |
| **`file filename`** | Commonly used without any options |
```bash
file secrets.txt               #prints out the file type of secrets.txt
```

|<a id="cp-anc"></a> Command | Common Options |
| --- | --- |
| **`cp [option(s)] sourcefile targetfile`** | -r   Copies directories recursively<br>-T   Treat destination as normal file | 
```bash
#first argument is the file being copied, second argument is where to copy the file
cp secrets.txt secrets2.txt           #creates a copy of secrets.txt, named secrets2.txt, in current working directory
cp secrets.txt /root/Desktop          #copies secrets.txt to /root/Desktop
cp secrets.txt -T secret              #copies secrets.txt to a new file named secret
cp -r /root/Documents /root/newdir    #recursively copies entire /root/Documents directory to a new directory call newdir located under /root
```

|<a id="mv-anc"></a> Command | Common Options |
| --- | --- |
| **`mv sourcefile targetfile`** | Commonly used without any options |
```bash
mv secrets.txt old_secrets.txt        #renames secrets.txt to old_secrets.txt
mv secrets.txt /root/Desktop          #moves secrets.txt to /root/Desktop directory
```

|<a id="rm-anc"></a> Command | Common Options |
| --- | --- |
| **`rm [options(s)] filename`** | -r  Removes directories and their contents recursively <br>-f  Force removes file |
```bash
rm secrets.txt                        #deletes the file secrets.txt
rm -r /root/newdir                    #deletes the directory /root/newdir and all its contents
rm -rf /root/newdir                   #force removes the entire directory /root/newdir
```

|<a id="echo-anc"></a> Command | Common Options |
| --- | --- |
| **`echo [text] [>> filename]`** | Commonly add `>> filename` after text to append to the end of the file. |
```bash
echo Display this text                        #Writes contents "Display this text" to console
echo Add this text to file >> secrets.txt     #Appends contents "Add this text to file" to the end of the file secrets.txt. Will create and add to the file if file doesn't exist.
```
|<a id="nano-anc"></a> Command |
| --- |
| **`nano`** & **`vi`** |
```bash
nano                          #opens nano editor
vi                            #opens vi editor
nano secrets.txt              #opens nano editor for file name secrets.txt
```

|<a id="ln-anc"></a> Command | Common Options |
| --- | --- |
| **`ln [option(s)] sourcefile targetfile`** | -s   Creates a symbolic link, enabling linking across file systems/partitions. Also allows linking of directories. |
```bash
ln secrets.txt linked_secrets.txt       #creates a hard link for secrets.txt called linked_secrets.txt
ln -s /root/Desktop/script.sh /bin/scriptcommand    #creates a soft link between script.sh located in /root/Desktop/ directory and scriptcommand located in /bin/ directory. This allows scriptcommand to be called from anywhere in the file system, since /bin/ is located in everyone's PATH..
```

|<a id="chmod-anc"></a> Command | Common Options |
| --- | --- |
| **`chmod`** |  |
```bash

```

|<a id="chown-anc"></a> Command | Common Options |
| --- | --- |
| **`chown`** |  |
```bash

```

|<a id="gzip-anc"></a> Command | Common Options |
| --- | --- |
| **`gzip`** |  |
```bash

```

|<a id="tar-anc"></a> Command | Common Options |
| --- | --- |
| **`tar`** |  |
```bash

```

|<a id="zip-anc"></a> Command | Common Options |
| --- | --- |
| **`zip`** |  |
```bash

```

|<a id="unzip-anc"></a> Command | Common Options |
| --- | --- |
| **`unzip`** |  |
```bash

```

|<a id="diff-anc"></a> Command | Common Options |
| --- | --- |
| **`diff`** |  |
```bash

```

---

### File Systems 

<a id="fs-basic"></a>

| Basic Commands | Description | Man Page | Example |
| --- | --- | --- | --- |
| **`pwd`** | Displays current working directory. | [Link](http://man7.org/linux/man-pages/man1/pwd.1.html) | [Jump to Example](#pwd-anc) |
| **`cd`** | Traverse to specific directory. | none | [Jump to Example](#cd-anc) |
| **`ls`** | Prints directories and files in a directory. | [Link](http://man7.org/linux/man-pages/man1/ls.1.html) | [Jump to Example](#ls-anc) |
| **`lsof`** | | [Link]() | [Jump to Example](#lsof-anc) |
| **`mkdir`** | Creates directory. | [Link](http://man7.org/linux/man-pages/man1/mkdir.1.html) | [Jump to Example](#mkdir-anc) |
| **`rmdir`** | Removes empty directory. | [Link](http://man7.org/linux/man-pages/man1/rmdir.1.html) | [Jump to Example](#rmdir-anc) |
| **`locate`** | Locates file on system based on the file name database. Will need to use **`updatedb`** if file was created after last database update. | [Link](http://man7.org/linux/man-pages/man1/locate.1.html) | [Jump to Example](#locate-anc) |
| **`updatedb`** | Command for updating file name database. | [Link](http://man7.org/linux/man-pages/man1/updatedb.1.html) | [Jump to Example](#updatedb-anc) |

<a id="fs-inter"></a>

| Intermediate Commands | Description | Man Page | Example |
| --- | --- | --- | --- |
| **`find`** | | [Link]() | [Jump to Example](#find-anc) |
| **`grep`** | | [Link]() | [Jump to Example](#grep-anc) |
| **`mount`** | | [Link]() | [Jump to Example](#mount-anc) |
| **`umount`** | | [Link]() | [Jump to Example](#umount-anc) |

<a id="fs-ex"></a>

#### Examples

|<a id="pwd-anc"></a> Command | Common Options |
| --- | --- |
| **`pwd`** | Command that doesn't use options |
```bash
pwd               #displays current directory
```

|<a id="cd-anc"></a> Command | Common Options |
| --- | --- |
| **`cd [directory]`** | |
```bash
cd /root/Desktop  #go to Desktop folder under root
cd ..             #take a step up the directory tree, would return to /root/
cd                #return to home directory no matter where location, returns to /root/ in this case
```

|<a id="ls-anc"></a> Command | Common Options |
| --- | --- |
| **`ls`** | |
```bash
ls                      #prints directories/files listed under current directory
ls -l                   #prints current directories/files with permissions
ls -a                   #prints current d/f plus hidden files
ls /root/Desktop        #prints d/f under /root/Desktop
ls -r /root/Desktop     #prints /root/Desktop and recursively prints all directories under /root/Desktop
```

|<a id="lsof-anc"></a> Command | Common Options |
| --- | --- |
| **`lsof`** |  |
```bash

```

|<a id="mkdir-anc"></a> Command | Common Options |
| --- | --- |
| **`mkdir`** | |
```bash
mkdir folder1                 #creates directory named 'folder1' under current directory
mkdir /root/Desktop/folder1   #creates directory named 'folder1' under /root/Desktop
```

|<a id="rmdir-anc"></a> Command | Common Options |
| --- | --- |
| **`rmdir`** | |
```bash
rmdir folder1                 #removes empty directory 'folder1' in current directory
rmdir /root/Desktop/folder1   #removes empty directory 'folder1' under /root/Desktop
```

|<a id="locate-anc"></a> Command | Common Options |
| --- | --- |
| **`locate`** | -i   Ignores case <br> |
```bash
locate secrets.txt            #will search file name database for files with secrets.txt in name
locate -i screts.txt          #will search file name database for any file, regardless of case, with secrets.txt in name
```

|<a id="updatedb-anc"></a> Command | Common Options |
| --- | --- |
| **`updatedb`** | Commonly used without any options |
```bash
updatedb                      #updates file name database for locate
```

|<a id="find-anc"></a> Command | Common Options |
| --- | --- |
| **`find`** |  |
```bash

```

|<a id="grep-anc"></a> Command | Common Options |
| --- | --- |
| **`grep`** |  |
```bash

```

|<a id="mount-anc"></a> Command | Common Options |
| --- | --- |
| **`mount`** |  |
```bash

```

|<a id="umount-anc"></a> Command | Common Options |
| --- | --- |
| **`umount`** |  |
```bash

```

---

## System Commands
**_Some commands used for system and network information._**

### System

<a id="s-basic"></a>

| Basic Commands | Description | Man Page | Example |
| --- | --- | --- | --- |
| **`uname`** | | [Link]() | [Jump to Example](#uname-anc) |
| **`hostname`** | | [Link]() | [Jump to Example](#hostname-anc) |
| **`users`** | | [Link]() | [Jump to Example](#users-anc) |
| **`who`** | | [Link]() | [Jump to Example](#who-anc) |
| **`whoami`** | | [Link]() | [Jump to Example](#whoami-anc) |
| **`sudo`** | Using sudo before another command will run it with root privilege. Will need to enter root password after running command. | [Link]() | [Jump to Example](#sudo-anc) |
| **`su`** | Upgrades privilege to root. Root password will need to be set to use and will need to enter root password to be able to elevate. | [Link]() | [Jump to Example](#su-anc) |
| **`date`** | | [Link]() | [Jump to Example](#date-anc) |
| **`uptime`** | | [Link]() | [Jump to Example](#uptime-anc) |
| **`passwd`** | | [Link]() | [Jump to Example](#passwd-anc) |
| **`apt-get`** | | [Link]() | [Jump to Example](#apt-get-anc) |
| **`halt`** | | [Link]() | [Jump to Example](#halt-anc) |
| **`reboot`** | | [Link]() | [Jump to Example](#reboot-anc) |

<a id="s-inter"></a>

| Intermediate Commands | Description | Man Page | Example |
| --- | --- | --- | --- |
| **`top`** | | [Link]() | [Jump to Example](#top-anc) |
| **`last`** | | [Link]() | [Jump to Example](#last-anc) |
| **`ps`** | | [Link]() | [Jump to Example](#ps-anc) |
| **`df`** | | [Link]() | [Jump to Example](#df-anc) |
| **`du`** | | [Link]() | [Jump to Example](#du-anc) |
| **`free`** | | [Link]() | [Jump to Example](#free-anc) |
| **`crontab`** | | [Link]() | [Jump to Example](#crontab-anc) |
| **`service`** | | [Link]() | [Jump to Example](#service-anc) |
| **`kill`** | | [Link]() | [Jump to Example](#kill-anc) |
| **`killall`** | | [Link]() | [Jump to Example](#killall-anc) |

<a id="s-ex"></a>

#### Examples

|<a id="uname-anc"></a> Command | Common Options |
| --- | --- |
| **`uname`** |  |
```bash

```

|<a id="hostname-anc"></a> Command | Common Options |
| --- | --- |
| **`hostname`** |  |
```bash

```

|<a id="users-anc"></a> Command | Common Options |
| --- | --- |
| **`users`** |  |
```bash

```

|<a id="who-anc"></a> Command | Common Options |
| --- | --- |
| **`who`** |  |
```bash

```

|<a id="whoami-anc"></a> Command | Common Options |
| --- | --- |
| **`whoami`** |  |
```bash

```

|<a id="sudo-anc"></a> Command | Common Options |
| --- | --- |
| **`sudo`** |  |
```bash
sudo apt-get update           #updating system with root permission
```

|<a id="su-anc"></a> Command | Common Options |
| --- | --- |
| **`su`** |  |
```bash
su                            #elevate access to root
sudo passwd                   #set new root password
```

|<a id="date-anc"></a> Command | Common Options |
| --- | --- |
| **`date`** |  |
```bash

```

|<a id="uptime-anc"></a> Command | Common Options |
| --- | --- |
| **`uptime`** |  |
```bash

```

|<a id="passwd-anc"></a> Command | Common Options |
| --- | --- |
| **`passwd`** |  |
```bash

```

|<a id="apt-get-anc"></a> Command | Common Options |
| --- | --- |
| **`apt-get`** |  |
```bash

```

|<a id="halt-anc"></a> Command | Common Options |
| --- | --- |
| **`halt`** |  |
```bash

```

|<a id="reboot-anc"></a> Command | Common Options |
| --- | --- |
| **`reboot`** |  |
```bash

```

|<a id="top-anc"></a> Command | Common Options |
| --- | --- |
| **`top`** |  |
```bash

```

|<a id="last-anc"></a> Command | Common Options |
| --- | --- |
| **`last`** |  |
```bash

```

|<a id="ps-anc"></a> Command | Common Options |
| --- | --- |
| **`ps`** |  |
```bash

```

|<a id="df-anc"></a> Command | Common Options |
| --- | --- |
| **`df`** |  |
```bash

```

|<a id="du-anc"></a> Command | Common Options |
| --- | --- |
| **`du`** |  |
```bash

```

|<a id="free-anc"></a> Command | Common Options |
| --- | --- |
| **`free`** |  |
```bash

```

|<a id="crontab-anc"></a> Command | Common Options |
| --- | --- |
| **`crontab`** |  |
```bash

```

|<a id="service-anc"></a> Command | Common Options |
| --- | --- |
| **`service`** |  |
```bash

```

|<a id="kill-anc"></a> Command | Common Options |
| --- | --- |
| **`kill`** |  |
```bash

```

|<a id="killall-anc"></a> Command | Common Options |
| --- | --- |
| **`killall`** |  |
```bash

```

---

### Networking

<a id="net-basic"></a>

| Basic Commands | Description | Man Page | Example |
| --- | --- | --- | --- |
| **`ping`** | | [Link]() | [Jump to Example](#ping-anc) |
| **`ifconfig`** | | [Link]() | [Jump to Example](#ifconfig-anc) |
| **`host`** | | [Link]() | [Jump to Example](#host-anc) |
| **`arp`** | | [Link]() | [Jump to Example](#arp-anc) |
| **`dig`** | | [Link]() | [Jump to Example](#dig-anc) |
| **`route`** | | [Link]() | [Jump to Example](#route-anc) |
| **`nslookup`** | | [Link]() | [Jump to Example](#nslookup-anc) |
| **`netstat`** | | [Link]() | [Jump to Example](#netstat-anc) |
| **`wget`** | | [Link]() | [Jump to Example](#wget-anc) |

<a id="net-inter"></a>

| Intermediate Commands | Description | Man Page | Example |
| --- | --- | --- | --- |
| **`scp`** | | [Link]() | [Jump to Example](#scp-anc) |
| **`ftp`** | | [Link]() | [Jump to Example](#ftp-anc) |
| **`sftp`** | | [Link]() | [Jump to Example](#sftp-anc) |
| **`ssh`** | | [Link]() | [Jump to Example](#ssh-anc) |
| **`nmap`** | | [Link]() | [Jump to Example](#nmap-anc) |
| **`tcpdump`** | | [Link]() | [Jump to Example](#tcpdump-anc) |
| **`telnet`** | | [Link]() | [Jump to Example](#telnet-anc) |
| **`whois`** | | [Link]() | [Jump to Example](#whois-anc) |
| **`traceroute`** | | [Link]() | [Jump to Example](#traceroute-anc) |
| **`tracepath`** | | [Link]() | [Jump to Example](#tracepath-anc) |
| **`ifup`** | | [Link]() | [Jump to Example](#ifup-anc) |
| **`ifdown`** | | [Link]() | [Jump to Example](#ifdown-anc) |
| **`dhclient`** | | [Link]() | [Jump to Example](#dhclient-anc) |

<a id="net-ex"></a>

#### Examples

|<a id="ping-anc"></a> Command | Common Options |
| --- | --- |
| **`ping`** |  |
```bash

```

|<a id="ifconfig-anc"></a> Command | Common Options |
| --- | --- |
| **`ifconfig`** |  |
```bash

```

|<a id="host-anc"></a> Command | Common Options |
| --- | --- |
| **`host`** |  |
```bash

```

|<a id="arp-anc"></a> Command | Common Options |
| --- | --- |
| **`arp`** |  |
```bash

```

|<a id="dig-anc"></a> Command | Common Options |
| --- | --- |
| **`dig`** |  |
```bash

```

|<a id="route-anc"></a> Command | Common Options |
| --- | --- |
| **`route`** |  |
```bash

```

|<a id="nslookup-anc"></a> Command | Common Options |
| --- | --- |
| **`nslookup`** |  |
```bash

```

|<a id="netstat-anc"></a> Command | Common Options |
| --- | --- |
| **`netstat`** |  |
```bash

```

|<a id="scp-anc"></a> Command | Common Options |
| --- | --- |
| **`scp`** |  |
```bash

```

|<a id="ftp-anc"></a> Command | Common Options |
| --- | --- |
| **`ftp`** |  |
```bash

```

|<a id="sftp-anc"></a> Command | Common Options |
| --- | --- |
| **`sftp`** |  |
```bash

```

|<a id="ssh-anc"></a> Command | Common Options |
| --- | --- |
| **`ssh`** |  |
```bash

```

|<a id="nmap-anc"></a> Command | Common Options |
| --- | --- |
| **`nmap`** |  |
```bash

```

|<a id="tcpdump-anc"></a> Command | Common Options |
| --- | --- |
| **`tcpdump`** |  |
```bash

```

|<a id="telnet-anc"></a> Command | Common Options |
| --- | --- |
| **`telnet`** |  |
```bash

```

|<a id="whois-anc"></a> Command | Common Options |
| --- | --- |
| **`whois`** |  |
```bash

```

|<a id="traceroute-anc"></a> Command | Common Options |
| --- | --- |
| **`traceroute`** |  |
```bash

```

|<a id="tracepath-anc"></a> Command | Common Options |
| --- | --- |
| **`tracepath`** |  |
```bash

```

|<a id="ifup-anc"></a> Command | Common Options |
| --- | --- |
| **`ifup`** |  |
```bash

```

|<a id="ifdown-anc"></a> Command | Common Options |
| --- | --- |
| **`ifdown`** |  |
```bash

```

|<a id="dhclient-anc"></a> Command | Common Options |
| --- | --- |
| **`dhclient`** |  |
```bash

```

---

## Other

### Random

_Random commands_

**`clear`** Clears the terminal
```bash
clear         #clears the terminal
```

**`exit`** Exits the current terminal windows
```bash
exit          #exits terminal window
```

### Shortcuts 

Using **`Ctrl+C`** will safely stop current execution

Using **`Ctrl+Z`** will force stop current execution

---

## Resources

| Basic Guides | Description |
| --- | --- |
| [Guide](https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners) | A guide for commonly used Linux commands, aimed at beginners. |
| [Guide](https://www-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.0/userguide-9.0/ch24s04.html) | A guide for a mix between basic and intermediate commonly used Linux commands. |

| Intermediate Guides | Description |
| --- | --- |
| [Guide](https://blog.g0tmi1k.com/2011/08/basic-linux-privilege-escalation/) | A guide written for Linux privilege escalation. This guide does a great job describing many different ways to find information on Linux systems. |

| Other | Description |
| --- | --- |
| [Link](http://man7.org/linux/man-pages/dir_all_by_section.html#man1) | Linux man pages. |
