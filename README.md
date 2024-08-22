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
```

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

### 1. Backup Script
This script creates a backup of specified directories and compresses them into a tarball with a timestamp.
```
#!/bin/bash

# Directories to backup
backup_dirs="/var/www /etc /home/user"

# Backup destination directory
backup_dest="/backup"

# Create backup directory if it doesn't exist
mkdir -p "$backup_dest"

# Backup filename with timestamp
backup_file="backup-$(date +%Y%m%d%H%M%S).tar.gz"

# Perform backup
tar -czvf "$backup_dest/$backup_file" $backup_dirs

# Optionally, clean up old backups (e.g., keep last 7 days)
find "$backup_dest" -name "backup-*" -mtime +7 -exec rm {} \;
```

### 2. Log Rotation Script
This script rotates logs and archives older log files to save disk space.

```
#!/bin/bash

# Log directory
log_dir="/var/log/app"

# Maximum number of log files to keep
max_logs=5

# Rotate and compress logs
for logfile in $(ls -t $log_dir/*.log | tail -n +$max_logs); do
    gzip -9 "$logfile"
done

# Remove compressed logs older than 7 days
find $log_dir/*.log.gz -mtime +7 -exec rm {} \;
```

### 3. System Maintenance Script
This script performs routine maintenance tasks such as updating packages and cleaning up temporary files.

```
#!/bin/bash

# Update package lists and upgrade packages
apt-get update
apt-get upgrade -y

# Clean up unused packages and old kernels
apt-get autoremove -y
apt-get autoclean

# Clear temporary files
rm -rf /tmp/*

# Optionally, reboot the system if required
# reboot
```

### 4. Service Monitoring Script
This script checks the status of critical services and restarts them if they are not running.

```
#!/bin/bash
# List of services to monitor
services=("apache2" "mysql")

# Check status and restart if necessary
for service in "${services[@]}"; do
    systemctl is-active --quiet $service
    if [ $? -ne 0 ]; then
        systemctl start $service
        echo "Service $service restarted at $(date)" >> /var/log/service-monitor.log
    fi
done
```

### Tips for Using Shell Scripts in Production:
- **Permissions:** Ensure scripts have appropriate permissions (chmod +x script.sh) and are run with appropriate privileges.
- **Testing:** Test scripts in a non-production environment before deploying them to production.
- **Logging:** Implement logging to track script executions and outputs.
- **Error Handling:** Include error checking and handling to manage unexpected conditions gracefully.
- **Security:** Avoid hardcoding sensitive information (e.g., passwords) directly into scripts; use environment variables or secure vaults.

