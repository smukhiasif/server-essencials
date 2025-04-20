
# 🐧 Basic Linux Commands Reference

## 📁 File & Directory Commands

# List files in current directory
```bash
ls
```
# List files with detailed info
```bash
ls -l
```
# List all files including hidden
```bash
ls -a
```
# Change to another directory
```bash
cd /path/to/directory
```
# Show current directory
```bash
pwd
```
# Create a new directory
```bash
mkdir my_folder
```
# Remove an empty directory
```bash
rmdir old_folder
```
# Remove a directory and its contents
```bash
rm -r my_folder
```
# Create an empty file
```bash
touch file.txt
```
# Copy file or directory
```bash
cp source.txt destination.txt
```
# Move or rename file
```bash
mv oldname.txt newname.txt
```
# Delete a file
```bash
rm file.txt
```

## 📄 File Content


# Show file content
```bash
cat file.txt
```
# Scrollable file view
```bash
less file.txt
```
# Show first 10 lines
```bash
head file.txt
```
# Show last 10 lines
```bash
tail file.txt
```
# Monitor file in real-time
```bash
tail -f /var/log/syslog
```
# Edit file with Nano
```bash
nano file.txt
```
# Edit file with Vim
```bash
vim file.txt
```

## 🛠️ File Permissions


# Change permissions (read/write/execute for owner)
```bash
chmod 755 script.sh
```
# Change owner to user and group
```bash
chown username:groupname file.txt
```
# View file permissions
```bash
ls -l
```

## 📦 Package Management (Debian/Ubuntu)


# Update package list
```bash
sudo apt update
```
# Upgrade all packages
```bash
sudo apt upgrade
```
# Install a package
```bash
sudo apt install nginx
```
# Remove a package
```bash
sudo apt remove nginx
```
# Install a .deb package
```bash
sudo dpkg -i package.deb
```

## ⚙️ System Information

`
# Show kernel and system info
```bash
uname -a
```
# Display running processes
```bash
top
```
# Interactive process viewer (install first)
```bash
htop
```
# Show disk usage
```bash
df -h
```
# Show RAM usage
```bash
free -h
```
# System uptime
```bash
uptime
```
# Current username
```bash
whoami
```
# UID and GID info
```bash
id
```

## 👤 User Management

# Add new user
```bash
sudo adduser john
```
# Set password
```bash
sudo passwd john
```
# Delete user
```bash
sudo deluser john
```
# Switch to another user
```bash
su - john
```
# Run command as superuser
```bash
sudo apt update
```

## 🌐 Networking

# Ping a host
```bash
ping google.com
```
# Show network interfaces
```bash
ifconfig     # OR
ip a
```
# Show open ports
```bash
netstat -tuln
```
# Fetch content from URL
```bash
curl https://example.com
```
# Download file
```bash
wget https://example.com/file.zip
```

## 🔍 Searching

# Search for a file
```bash
find /home -name "notes.txt"
```
# Search text inside file
```bash
grep "keyword" file.txt
```
# Locate file (after `sudo updatedb`)
```bash
locate notes.txt
```

## 📦 Archive & Compression


# Compress a folder
```bash
tar -czvf archive.tar.gz folder/
```
# Extract tar.gz file
```bash
tar -xzvf archive.tar.gz
```
# Create zip archive
```bash
zip -r archive.zip folder/
```
# Unzip archive
```bash
unzip archive.zip
```

# 🔐 1. pam_faillock or pam_tally2 (Fail Locking)
 ## ✅ Check current status:
```
sudo faillog -u username
# OR
sudo pam_tally2 -u username
```

## ✅ To unlock the user:

```
sudo faillog -r -u username
# OR (older systems)
sudo pam_tally2 -u username -r
```

# 🚫 2. Manual Lock in /etc/shadow
```
sudo grep '^username' /etc/shadow
```

# ✅ Unlock manually (if starts with !):

```
sudo passwd -u username
```

# 🔐 3. fail2ban Blocking SSH Login
## ✅ Check banned IPs:
```
sudo fail2ban-client status sshd
```

## ✅ Unban an IP:
```
sudo fail2ban-client set sshd unbanip <IP_ADDRESS>
```

## ✅ 4. Check for SSH Daemon Restrictions
```
sudo nano /etc/ssh/sshd_config
```

## Look for:
```
DenyUsers username
AllowUsers username
```

## Remove or correct lines if needed, then:
```
sudo systemctl restart sshd
```

## 🧪 Diagnostic Script Snippet
### Want a quick unlock + diagnostic? Here's a Bash one-liner:
```
username="youruser"
sudo pam_tally2 -u $username
sudo pam_tally2 -u $username -r
sudo passwd -u $username
```

