# Linux Fundamental Commands

This repository contains a comprehensive list of fundamental Linux commands that are commonly used in Bash, SH, and other UNIX shells.

## Table of Contents

- [Navigation](#navigation)
- [File Management](#file-management)
- [Text Processing](#text-processing)
- [System Information](#system-information)
- [User Management](#user-management)
- [Network](#network)
- [Package Management](#package-management)
- [Permissions](#permissions)
- [Processes](#processes)
- [Miscellaneous](#miscellaneous)
- [Sample Shell Scripts](#Sample-Shell-Scripts)


## Navigation

- **cd:** Change directory.
  ```bash
  cd path/to/directory

- **ls:** List directory contents.
```
ls
ls -l
ls -a
```

- **pwd:** Print working directory.

```
pwd
```

## File Management

- **cp:** Copy files and directories.
```
cp source_file destination_file
```
- **mv:** Move or rename files and directories.
```
mv old_file new_file
mv file /path/to/directory
```
- **rm:** Remove files and directories.
```
rm file
rm -r directory
```
- **mkdir:** Create directories.
```
mkdir directory_name
```
- **rmdir:** Remove empty directories.
```
rmdir directory_name
```

## Text Processing

- **cat:** Concatenate and display files.
```
cat filename
```
- **grep:** Search for patterns in files.
```
grep pattern filename

- **sed:** Stream editor for text transformation.
```
sed 's/old/new/' filename
```
- **awk:** Pattern scanning and processing language.
```
awk '/pattern/ { print $1 }' filename
```

## System Information

- **uname:** Print system information.
```
uname -a
```
**df:** Display disk space usage.
```
df -h
```
**free:** Display amount of free and used memory.
```
free -h
```


## User Management

- **whoami:** Print the current user.
```
whoami
```
- **who:** Display who is logged in.
```
who
```
- **passwd:** Change user password.
```
passwd
```

## Network

- **ping:** Check the network connection to a server.
```
ping server_name
```
- **ifconfig / ip:** Display and configure network interfaces.
```
ifconfig
ip addr show
```
- **wget:** Non-interactive network downloader.
```
wget URL
```

##  Package Management

- **apt-get:** Command-line package handling utility (Debian-based).
```
sudo apt-get install package_name
```
- **yum:** Package manager for RPM-based distributions.
```
sudo yum install package_name
```

- the command to  download a file from internet or over a network:
```
wget URL
curl URL -o outputfile
```

## Permissions

- **chmod:** Change file permissions.
```
chmod permissions filename
```
- **chown:** Change file owner and group.
```
chown user:group filename
```
- sudo -i or sudo su - are equivalent commands. These commands start a new shell as the superuser (root) with root's environment variables and settings.
```
sudo -i: This command starts an interactive shell session as the root user, loading root's environment variables.
sudo su -: This is an alternative syntax to achieve the same result—switching to the root user with a login shell.
```
- sudo su allows you to switch to another user account. It invokes the su command with superuser privileges granted by sudo, enabling you to log in as another user.
```
It's generally followed by - <username> to switch to a specific user account,
for example, sudo su - john to switch to user john's environment.
```
- sudo -u <username> executes a command as a specified user.

```
sudo -u <username> command: This executes command as the user <username>.
```

## Processes

- **ps:** Report a snapshot of current processes.
```
ps aux
```
- **kill:** Send a signal to a process.
```
kill PID
```
- **top / htop:** Display Linux tasks.

```
top
htop
```


## Miscellaneous

- **date:** Print or set the system date and time.
```
date
```
- **history:** Command history.
```
history
```
- **tar:** Archive files.

```
tar -cvf archive_name.tar directory_to_compress
```


## Sample Shell Scripts
