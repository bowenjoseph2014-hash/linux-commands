# Linux Tips and Tricks - Arch Linux Edition

A comprehensive guide to essential Linux commands and utilities for Arch Linux users, including installation methods and usage examples.

---

## Table of Contents
1. [System Information Commands](#system-information-commands)
2. [Package Management](#package-management)
3. [File and Directory Operations](#file-and-directory-operations)
4. [System Performance](#system-performance)
5. [Networking](#networking)
6. [Useful Utilities](#useful-utilities)
7. [Arch Linux Specific Tools](#arch-linux-specific-tools)

---

## System Information Commands

### Neofetch - Display System Information with Style
Neofetch is a command-line system information tool that displays your OS, kernel, uptime, and more with ASCII art.

**Installation on Arch Linux:**
```bash
sudo pacman -S neofetch
```

**Usage:**
```bash
neofetch
```

**Output includes:**
- OS and kernel version
- Uptime
- Packages installed
- Shell
- Resolution
- CPU and GPU info
- Memory usage
- Terminal colors

**Customize your neofetch display:**
```bash
# Hide specific information
neofetch --hide kernel shell uptime

# Show only specific information
neofetch --off kernel shell
```

---

### Screenfetch - ASCII Distro Art Display
Similar to neofetch but with different ASCII art styles.

**Installation:**
```bash
sudo pacman -S screenfetch
```

**Usage:**
```bash
screenfetch
```

---

### `uname` - Unix Name
Display system information.

```bash
# Show all system information
uname -a

# Show kernel release
uname -r

# Show kernel name
uname -s

# Show hardware platform
uname -m
```

**Output Example:**
```
Linux arch-machine 6.1.25-arch1-1 #1 SMP PREEMPT_DYNAMIC Fri, 12 May 2023 x86_64 GNU/Linux
```

---

### `hostnamectl` - Control System Hostname
View and change your system's hostname.

```bash
# Display current hostname information
hostnamectl

# Set a new hostname (requires root)
sudo hostnamectl set-hostname "new-hostname"

# Set static and pretty hostname
sudo hostnamectl set-hostname --static "arch-machine"
sudo hostnamectl set-hostname --pretty "My Arch Machine"
```

---

### `lsb_release` - Distribution Information
Display distribution-specific information.

```bash
# Show distribution information
lsb_release -a

# Show description only
lsb_release -d
```

---

## Package Management

### Pacman - Arch Package Manager
Pacman is Arch Linux's native package manager.

**Basic Operations:**
```bash
# Update package database
sudo pacman -Sy

# Update all packages
sudo pacman -Syu

# Install a package
sudo pacman -S package_name

# Install multiple packages
sudo pacman -S package1 package2 package3

# Remove a package
sudo pacman -R package_name

# Remove package and dependencies
sudo pacman -Rns package_name

# Search for a package
pacman -Ss keyword

# Search installed packages
pacman -Qs keyword

# List all installed packages
pacman -Q

# Show package information
pacman -Si package_name

# Show local package information
pacman -Qi package_name

# Clean package cache
sudo pacman -Sc

# Full system cleanup (remove unused packages)
sudo pacman -Rns $(pacman -Qdtq)
```

---

### AUR (Arch User Repository) - yay
Install packages from AUR using yay helper.

**Installation:**
```bash
sudo pacman -S yay
```

**Usage:**
```bash
# Search AUR
yay -Ss keyword

# Install from AUR
yay -S aur_package

# Update all packages including AUR
yay -Syu
```

---

## File and Directory Operations

### `ls` - List Directory Contents
List files and directories with various options.

```bash
# Basic listing
ls

# Long format with details
ls -l

# Show hidden files
ls -a

# Long format with hidden files
ls -la

# Sort by modification time
ls -lt

# Sort by size
ls -lS

# Reverse sort order
ls -lr

# Show file sizes in human-readable format
ls -lh

# Show total size of directory
ls -lhS

# Recursive listing
ls -R
```

---

### `cd` - Change Directory
Navigate between directories.

```bash
# Change to home directory
cd ~
cd

# Change to parent directory
cd ..

# Change to previous directory
cd -

# Change to specific path
cd /path/to/directory
```

---

### `mkdir` - Make Directories
Create new directories.

```bash
# Create single directory
mkdir dirname

# Create multiple directories
mkdir dir1 dir2 dir3

# Create nested directories
mkdir -p /path/to/nested/directories

# Create with specific permissions
mkdir -m 755 dirname
```

---

### `cp` - Copy Files and Directories
Copy files and directories.

```bash
# Copy file
cp source.txt destination.txt

# Copy with verbose output
cp -v source.txt destination.txt

# Copy directory recursively
cp -r source_dir/ destination_dir/

# Preserve file attributes
cp -p source.txt destination.txt

# Copy and preserve everything
cp -a source_dir/ destination_dir/
```

---

### `mv` - Move/Rename Files
Move or rename files and directories.

```bash
# Move file to directory
mv file.txt /path/to/directory/

# Rename file
mv oldname.txt newname.txt

# Move multiple files
mv file1 file2 file3 /destination/

# Move directory
mv old_dir/ new_dir/
```

---

### `rm` - Remove Files
Delete files and directories.

```bash
# Remove file
rm filename

# Remove multiple files
rm file1 file2 file3

# Remove directory and contents
rm -r directory/

# Force remove without confirmation
rm -f filename

# Interactive removal
rm -i filename
```

---

### `find` - Search for Files
Find files and directories with various criteria.

```bash
# Find by name
find . -name "filename"

# Find by type (f=file, d=directory)
find . -type f

# Find by size
find . -size +100M

# Find by modification time
find . -mtime -7  # Modified in last 7 days

# Find and execute command
find . -name "*.tmp" -exec rm {} \;

# Find with grep pattern
find . -name "*.log" -exec grep -l "error" {} \;
```

---

## System Performance

### `top` - Interactive Process Monitor
Monitor running processes and system resources in real-time.

```bash
# Launch top
top

# Key commands in top:
# q - quit
# k - kill process
# h - help
# M - sort by memory usage
# P - sort by CPU usage
# T - sort by time
```

---

### `htop` - Enhanced Process Monitor
A more user-friendly alternative to top.

**Installation:**
```bash
sudo pacman -S htop
```

**Usage:**
```bash
htop
```

---

### `free` - Display Memory Usage
Show RAM and swap memory usage.

```bash
# Display memory in bytes
free

# Display memory in human-readable format
free -h

# Display in megabytes
free -m

# Display in gigabytes
free -g

# Repeat every 2 seconds
free -h -s 2
```

---

### `df` - Disk Space Usage
Show disk space usage on mounted filesystems.

```bash
# Show disk usage
df

# Show in human-readable format
df -h

# Show in kilobytes
df -k

# Include filesystem type
df -T

# Show only specific filesystem
df -h /home
```

---

### `du` - Directory Space Usage
Calculate directory and file space usage.

```bash
# Show directory size
du -sh /path/to/directory

# Show all subdirectories
du -sh /path/to/directory/*

# Show size in human-readable format
du -h

# Show top 10 largest directories
du -sh * | sort -rh | head -10

# Summary of directory
du -s /path/to/directory
```

---

### `dmesg` - Kernel Messages
Display kernel and boot messages.

```bash
# Show all kernel messages
dmesg

# Show last 20 messages
dmesg | tail -20

# Show messages for specific device
dmesg | grep -i usb

# Clear kernel message buffer (requires root)
sudo dmesg -C
```

---

## Networking

### `ip` - IP Configuration
Modern networking configuration tool.

```bash
# Show all interfaces
ip addr show

# Show specific interface
ip addr show eth0

# Show IP addresses only
ip addr show | grep "inet "

# Show routing table
ip route show

# Set IP address (requires root)
sudo ip addr add 192.168.1.100/24 dev eth0

# Bring interface up/down
sudo ip link set eth0 up
sudo ip link set eth0 down
```

---

### `ping` - Test Network Connectivity
Send ICMP echo requests to test connectivity.

```bash
# Ping with default count
ping google.com

# Ping specific number of packets
ping -c 5 google.com

# Ping with timeout
ping -w 2000 google.com

# Continuous ping
ping google.com
```

---

### `ifconfig` - Interface Configuration (Legacy)
Legacy network configuration tool (ip is preferred).

```bash
# Show all interfaces
ifconfig

# Show specific interface
ifconfig eth0
```

---

### `curl` - Transfer Data with URLs
Download files and interact with web services.

```bash
# Download file
curl https://example.com/file.txt

# Save to specific filename
curl -o filename.txt https://example.com/file.txt

# Follow redirects
curl -L https://example.com

# Show response headers
curl -i https://example.com

# POST request
curl -X POST -d "data" https://example.com/api

# Add custom header
curl -H "Authorization: Bearer token" https://example.com/api
```

---

### `wget` - Download Files
Command-line file downloader.

**Installation:**
```bash
sudo pacman -S wget
```

**Usage:**
```bash
# Download file
wget https://example.com/file.zip

# Save with custom name
wget -O customname.zip https://example.com/file.zip

# Resume incomplete download
wget -c https://example.com/largefile.iso

# Download multiple files
wget https://example.com/file1.zip https://example.com/file2.zip

# Recursive download
wget -r https://example.com/directory/
```

---

## Useful Utilities

### `grep` - Search Text
Search for patterns in files.

```bash
# Simple search
grep "pattern" filename.txt

# Case-insensitive search
grep -i "PATTERN" filename.txt

# Recursive search in directory
grep -r "pattern" /path/to/directory/

# Show line numbers
grep -n "pattern" filename.txt

# Invert match (show non-matching lines)
grep -v "pattern" filename.txt

# Count matches
grep -c "pattern" filename.txt

# Search multiple patterns
grep -E "pattern1|pattern2" filename.txt
```

---

### `sed` - Stream Editor
Edit and transform text.

```bash
# Replace first occurrence in each line
sed 's/old/new/' filename.txt

# Replace all occurrences
sed 's/old/new/g' filename.txt

# Case-insensitive replacement
sed 's/old/new/gi' filename.txt

# Delete lines matching pattern
sed '/pattern/d' filename.txt

# Print specific lines
sed -n '1,5p' filename.txt  # Lines 1-5

# Edit file in place
sed -i 's/old/new/g' filename.txt
```

---

### `awk` - Text Processing
Process and analyze text files.

```bash
# Print specific columns
awk '{print $1, $3}' filename.txt

# Filter by condition
awk '$3 > 100 {print}' filename.txt

# Count lines
awk 'END {print NR}' filename.txt

# Print line if it contains pattern
awk '/pattern/ {print}' filename.txt

# Calculate sum
awk '{sum += $1} END {print sum}' numbers.txt
```

---

### `tar` - Archive Files
Create and extract compressed archives.

```bash
# Create tar archive
tar -cf archive.tar file1 file2 directory/

# Create gzip compressed archive
tar -czf archive.tar.gz file1 file2 directory/

# Create bzip2 compressed archive
tar -cjf archive.tar.bz2 file1 file2 directory/

# Extract archive
tar -xf archive.tar

# Extract gzip archive
tar -xzf archive.tar.gz

# Extract bzip2 archive
tar -xjf archive.tar.bz2

# List contents
tar -tzf archive.tar.gz

# Extract to specific directory
tar -xzf archive.tar.gz -C /path/to/directory/
```

---

### `zip` - Compress Files
Create ZIP archives.

```bash
# Create zip archive
zip archive.zip file1 file2

# Create zip recursively
zip -r archive.zip directory/

# Extract zip file
unzip archive.zip

# List zip contents
unzip -l archive.zip

# Extract to specific directory
unzip archive.zip -d /path/to/directory/
```

---

### `chmod` - Change Permissions
Modify file and directory permissions.

```bash
# Add execute permission
chmod +x filename

# Remove read permission
chmod -r filename

# Set specific permissions (numeric)
chmod 755 filename    # rwxr-xr-x

# Recursive permission change
chmod -R 755 directory/

# Common permission examples:
# 755 - Owner: rwx, Group: rx, Others: rx
# 644 - Owner: rw, Group: r, Others: r
# 700 - Owner: rwx, Group: none, Others: none
```

---

### `chown` - Change Owner
Modify file and directory owner.

```bash
# Change owner
sudo chown newuser filename

# Change owner and group
sudo chown newuser:newgroup filename

# Recursive change
sudo chown -R newuser:newgroup directory/
```

---

### `systemctl` - Manage System Services
Control and manage systemd services.

```bash
# Start service
sudo systemctl start service_name

# Stop service
sudo systemctl stop service_name

# Restart service
sudo systemctl restart service_name

# Enable service at boot
sudo systemctl enable service_name

# Disable service at boot
sudo systemctl disable service_name

# Check service status
systemctl status service_name

# List all services
systemctl list-units --type=service

# Check if service is enabled
systemctl is-enabled service_name

# Reload systemd daemon
sudo systemctl daemon-reload
```

---

### `journalctl` - View System Logs
Access systemd journal logs.

```bash
# Show recent logs
journalctl

# Show last 20 lines
journalctl -n 20

# Follow logs in real-time
journalctl -f

# Show logs for specific service
journalctl -u service_name

# Show logs since last boot
journalctl -b

# Show logs from specific date
journalctl --since "2024-01-01"

# Show logs with priority error or higher
journalctl -p err
```

---

## Arch Linux Specific Tools

### `pacman-contrib` - Pacman Utilities
Install additional pacman tools.

**Installation:**
```bash
sudo pacman -S pacman-contrib
```

**Useful commands:**
```bash
# Find packages occupying most space
pacman -Qi | awk '/^Name/{ name=$3 } /^Installed Size/{ print $4$5, name }' | sort -h | tail -20

# Check pacman stats
pacsearch neofetch

# Download database
sudo pacman -Sy
```

---

### `reflector` - Arch Mirror Manager
Optimize Arch Linux package mirrors for faster downloads.

**Installation:**
```bash
sudo pacman -S reflector
```

**Usage:**
```bash
# Find fastest mirrors
sudo reflector --latest 20 --sort rate --save /etc/pacman.d/mirrorlist

# Find mirrors from specific country
sudo reflector --country US --latest 10 --sort rate --save /etc/pacman.d/mirrorlist

# Verbose output
sudo reflector --latest 20 --sort rate --verbose
```

---

### `archlinux-keyring` - Keep Keys Updated
Maintain Arch Linux package signing keys.

**Installation:**
```bash
sudo pacman -S archlinux-keyring

# Update keys
sudo pacman-key --refresh-keys
```

---

### `base-devel` - Development Tools
Essential development tools for Arch Linux.

**Installation:**
```bash
sudo pacman -S base-devel
```

Includes: gcc, make, patch, pkg-config, etc.

---

## Pro Tips & Tricks

### 1. **Create Useful Aliases**
Add to your `~/.bashrc` or `~/.zshrc`:

```bash
# List with size
alias ll='ls -lh'

# System info
alias sysinfo='neofetch'

# Update system
alias update='sudo pacman -Syu && yay -Syu'

# Find large files
alias largef='find . -type f -size +100M'

# Check disk usage
alias diskusage='du -sh * | sort -rh'
```

---

### 2. **Quick Package Search**
```bash
# Find and install in one command
sudo pacman -S $(pacman -Ssq keyword | fzf --multi)
```

---

### 3. **Backup Before Updates**
```bash
# Create system backup
sudo tar -czf system-backup-$(date +%Y%m%d).tar.gz / --exclude=/proc --exclude=/sys
```

---

### 4. **View Real-time System Monitoring**
```bash
# Watch disk usage
watch -n 1 'df -h'

# Watch memory usage
watch -n 1 'free -h'
```

---

### 5. **Fast Directory Navigation**
```bash
# Jump back to previous directory
cd -

# Jump to home quickly
cd ~
```

---

## Common Issues & Solutions

### Package Conflicts
```bash
# Find conflicting packages
pacman -Qq | grep package_name

# Remove conflicting package
sudo pacman -Rdd package_name
```

### AUR Build Failures
```bash
# Clean build cache
yay -Sc

# Build without checking dependencies
yay -S --mflags --nodeps package_name
```

### Slow System
```bash
# Check what's using resources
htop

# Look at disk I/O
iostat -x 1

# Check system load
uptime

# Check running processes
ps aux | grep process_name
```

---

## Resources

- [Arch Linux Wiki](https://wiki.archlinux.org/)
- [Arch Linux Documentation](https://archlinux.org/docs/)
- [Pacman Manual](https://man.archlinux.org/man/pacman.8)
- [Systemd Manual](https://man.archlinux.org/man/systemd.1)

---

**Last Updated:** 2026

Happy Linux hacking! 🐧
