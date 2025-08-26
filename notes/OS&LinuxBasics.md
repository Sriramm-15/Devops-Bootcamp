## 1 - Operating Systems & Linux Basics

# Virtualization & Virtual Machines

### Hypervisor Requirement  
To run **multiple virtual machines (VMs)** on a **single physical computer**, a **hypervisor** is required.

### Popular Options  
- **VirtualBox** → one of the most commonly used hypervisors.  
  - ⚠️ Does **not support Apple’s M1 chips**.  
  - Alternative: **UTM** for those devices.  

### VM Isolation  
Each **Virtual Machine (VM)** operates in its own **isolated environment**, ensuring experiments inside a VM do **not affect the main operating system**.

---

## Types of Hypervisors  

### **Type 1 (Bare Metal)**  
- Runs **directly on the physical hardware**.  
- Often used in **servers**.  
- **Advantages:**  
  - **Better performance** & **hardware efficiency**.  
  - Supports **VMIs (Virtual Machine Images)**.  
  - Features like **snapshots & backups** for easy recovery.  

### **Type 2 (Hosted)**  
- Runs on top of a **host operating system**.  
- Commonly used for **personal learning & development**.  
- **Advantages:**  
  - Great for **experimentation & safe testing**, without risking the main OS.  
  - Can run applications across **different operating systems**.  

---

✨ **Summary:**  
- Use a **Type 2 Hypervisor** for learning and testing locally.  
- Use a **Type 1 Hypervisor** for **production environments** that require high performance, efficiency, and reliability.

# 🐧 Linux Basics & Commands

## 🔹 Linux File System
- In **Linux, everything is a file**  
  (In **Mac/Windows**, not everything is treated as a file).
- A **root user** has its own home directory.  
  - Example: On **Mac**, it is `/Users/<username>`  

### 📂 Linux Folder Structure
- `/home/{username}` → home directory for non-root users (if created with a home dir)  
- `/bin` → executables for **essential system commands**  
- `/sbin` → system binaries, require **superuser privileges**  
- `/lib` → shared libraries required by `/bin` and `/sbin`  
- `/usr` → originally used for user home dirs (historic reasons)  
- `/usr/local` → programs you install for **all users**  
- `/opt` → 3rd party programs (not split into components)  
- `/boot` → files required for **booting system**  
- `/etc` → system **config files**  
- `/dev` → device files (**webcam, mouse, keyboard, etc.**)  
- `/var` → **logs**, spool files  
- `/var/cache` → cached data  
- `/tmp` → temporary files, deleted on restart  
- `/media` → mount point for **removable media** (USB, DVD)  
- `/mnt` → temporary mount points  
- Hidden files start with a dot `.` (example: `~/.bashrc`)  

---

## 📝 Basic Linux Commands
- `pwd` → show current directory  
- `ls` → list contents  
- `cd <dir>` → change directory  
  - `cd /` → go to root dir  
  - `cd` (empty) → home dir  
- `mkdir <dir>` → make directory  
- `touch <file>` → create file  
- `rm <file>` → delete file  
- `rm -r <dir>` → delete directory (with files in it)  
- `rmdir <dir>` → delete empty dir  
- `clear` → clear terminal  
- `mv <old> <new>` → rename/move file  
- `cp -r <dir> <dest>` → copy folder with contents  
- `ls -R` → list all files recursively  
- `history` → show recent commands  
- `ls -a` → list hidden files  
- `ls -l` → list in long format (`ls -la` for hidden + long format)  
- `cat <file>` → print file content  
- `uname -a` → system & kernel info  
- `cat /etc/os-release` → Linux version info  
- `lscpu` → CPU info  
- `lsmem` → memory info  
- `sudo <command>` → run command with **super user** privileges  
- `su - <username>` → switch user  

---

## 🔀 Pipes & Redirection
- `|` → pipe, pass output of one command to another  
- `<command> | less` → view data page by page  
- `<command> | grep <pattern>` → filter by pattern  
- `>` → redirect (overwrite to file)  
- `>>` → redirect (append to file)  
- Multiple commands in one line → `cmd1 ; cmd2 ; cmd3`

---

## 📦 Package Manager (APT - Debian/Ubuntu)
APT manages software installation, dependencies, and updates.

- `apt search <package>` → search package  
- `apt install <package>` → install  
- `apt remove <package>` → uninstall  
- `apt update` → refresh package lists  
- `apt upgrade` → upgrade packages  
- `apt autoremove` → remove unused packages  
- `apt full-upgrade` → upgrade with dependencies  

---

## ✍️ VIM Text Editor (Basics)
- `:wq` → save & quit  
- `:q!` → quit without saving  
- `dd` → delete line  
- `d10d` → delete next 10 lines  
- `u` → undo  
- `A` → jump to end of line (insert mode)  
- `$` → jump to end of line (normal mode)  
- `0` → jump to start of line  
- `12G` → jump to line 12  
- `/pattern` → search  
- `n` → next match, `N` → previous match  
- `:%s/old/new/g` → replace all  

---

## 👤 Users, Groups & Permissions

### User Types
- **Root user** → superuser with full control  
- **Regular user** → standard users  
- **Service user** → restricted user accounts (e.g., for `docker`, `nexus`)  

### 🔧 User & Group Commands
- `adduser <username>` → add user  
- `passwd <username>` → set/change password  
- `su - <username>` → switch user  
- `su -` → switch to root  
- `groupadd <group>` → add group  
- `deluser <username>` → delete user  
- `groupdel <group>` → delete group  
- `usermod [options] <username>` → modify user  
  - `usermod -g <group> <username>` → change primary group  
  - `usermod -G <group> <username>` → set secondary groups (overwrites)  
  - `usermod -aG <group> <username>` → append secondary groups  
- `gpasswd -d <username> <group>` → remove user from group  
- `groups <username>` → list user groups  
- `exit` → logout  
- `chown <user>:<group> <file>` → set file ownership  
- `chgrp <group> <file>` → change group ownership  

---

## 🔐 File Permissions

Each file has 3 categories:  
1. **Owner**  
2. **Group**  
3. **Others**

- `r` = read  
- `w` = write  
- `x` = execute  
- `-` = no permission  

### Chmod Examples
- `chmod -x <file>` → remove execute for all  
- `chmod g-w <file>` → remove write for group  
- `chmod g+x <file>` → add execute for group  
- `chmod u+x <file>` → add execute for user  
- `chmod o+x <file>` → add execute for others  
- `chmod g=rwx <file>` → set full group permissions  
- `chmod 777 <file>` → all permissions for everyone  

---

✅ **Tip for Beginners:**  
- Always check file permissions with `ls -l`.  
- Use `man <command>` for detailed help (example: `man ls`).  
