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


## Navigation

- `cd`: Change directory.
  ```bash
  cd path/to/directory

  `ls`: List directory contents.
```
ls
ls -l
ls -a
```

- pwd: Print working directory.

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

