## **📌 Week 2: Linux Essentials for DevOps (Days 8-14)**  
Linux is the backbone of DevOps. Almost every tool in the DevOps ecosystem runs on Linux. This week, we will cover **Linux commands, file system, permissions, networking, process management, user management, and security**.  

---

## **🔹 Day 8: Linux Basics & Command Line (CLI)**  
### **📌 What is Linux?**  
Linux is an open-source operating system used for servers, cloud computing, and DevOps environments.  

### **📌 Important CLI Commands**  
- `pwd` → Print current directory  
- `ls -l` → List files with details  
- `cd /path` → Change directory  
- `mkdir folder` → Create a folder  
- `rm file` → Delete a file  
- `cp file1 file2` → Copy files  
- `mv file1 file2` → Move/Rename files  
- `cat file` → View file content  
- `echo "text" > file.txt` → Write text to a file  
- `man command` → Show manual for a command  

---

## **🔹 Day 9: File Management & Permissions**  
### **📌 Linux File System Structure**  
- `/home` → User home directories  
- `/etc` → System configuration files  
- `/var` → Log files  
- `/usr` → Installed programs  
- `/tmp` → Temporary files  

### **📌 File Permissions** (`rwx`)  
- `r` (Read)  
- `w` (Write)  
- `x` (Execute)  

### **📌 Change Permissions**  
- `chmod 755 script.sh` → Read/write/execute for owner, read/execute for others  
- `chown user:group file` → Change file owner  
- `ls -l file` → Check file permissions  

---

## **🔹 Day 10: Linux Networking Basics**  
### **📌 Check Network Configuration**  
- `ip a` → Show IP addresses  
- `ifconfig` → Show network interfaces  
- `netstat -tulnp` → Show open ports  
- `ping google.com` → Test connectivity  

### **📌 Firewall Management**  
- `ufw allow 22/tcp` → Allow SSH  
- `ufw enable` → Enable firewall  

---

## **🔹 Day 11: Process Management & Monitoring** 