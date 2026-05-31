# 🐧 Linux Tips & Tricks - Arch Edition

A comprehensive guide to essential Linux and Arch Linux commands with practical examples and usage tips.

## 🌐 View the Website

**[Click here to view the interactive website](https://bowenjoseph2014-hash.github.io/linux-commands/)**

> The website features a modern dark theme with interactive navigation, live search, and one-click code copying.

---

## 📚 Contents

This repository contains two versions of the Linux tips and tricks guide:

### 1. **Interactive Website** (`index.html`)
- Modern dark theme perfect for Linux users
- Live search functionality
- Smooth navigation between sections
- One-click copy to clipboard for all commands
- Fully responsive design (mobile, tablet, desktop)
- [View Online](https://bowenjoseph2014-hash.github.io/linux-commands/)

### 2. **Markdown Guide** (`LINUX_TIPS_AND_TRICKS.md`)
- Complete text-based reference
- Includes all commands and examples
- Easy to read in any text editor or markdown viewer

---

## 📖 Sections Covered

### System Information
- **Neofetch** - Display system info with ASCII art
- `uname` - Unix name and system information
- `hostnamectl` - Hostname configuration
- And more system info tools

### Package Management
- **Pacman** - Arch Linux package manager
- **AUR (yay)** - Arch User Repository
- Installation, updates, and cleanup commands

### File & Directory Operations
- `ls`, `cd`, `mkdir`, `cp`, `mv`, `rm`, `find`
- Comprehensive examples for each command
- Common use cases and tips

### System Performance
- `htop` - Process monitoring
- `free` - Memory usage
- `df` & `du` - Disk space analysis
- Real-time monitoring tips

### Networking
- `ip` - IP configuration
- `ping` - Connectivity testing
- `curl` & `wget` - File downloads
- Network configuration examples

### Useful Utilities
- `grep` - Text searching
- `sed` - Stream editing
- `tar` - Archive operations
- `chmod` & `chown` - Permission management

### Arch Linux Specific Tools
- `reflector` - Mirror optimization
- `systemctl` - Service management
- `journalctl` - System logging
- `base-devel` - Development tools

### Pro Tips & Tricks
- Custom aliases for productivity
- Quick package installation
- Real-time system monitoring
- Performance optimization

---

## 🚀 Quick Start

### Installation of Neofetch (Featured Tool)

```bash
sudo pacman -S neofetch
neofetch
```

### Update Your Arch System

```bash
sudo pacman -Syu
yay -Syu
```

### Install base-devel for Development

```bash
sudo pacman -S base-devel
```

---

## 💻 Using Pacman Commands

```bash
# Search for packages
pacman -Ss keyword

# Install a package
sudo pacman -S package_name

# Remove a package
sudo pacman -R package_name

# Update all packages
sudo pacman -Syu
```

---

## 🎨 Website Features

- ✨ **Modern Dark Theme** - Easy on the eyes
- 🔍 **Live Search** - Find commands quickly
- ⌨️ **Copy to Clipboard** - One-click code copying
- 📱 **Responsive Design** - Works on all devices
- 🎯 **Smooth Navigation** - Quick section jumping
- 💡 **Interactive Examples** - Real-world use cases

---

## 📝 How to Use This Repository

1. **Online**: Visit the [interactive website](https://bowenjoseph2014-hash.github.io/linux-commands/)
2. **Local**: Clone and open `index.html` in your browser
3. **Reference**: Read `LINUX_TIPS_AND_TRICKS.md` for detailed information

### Clone the Repository

```bash
git clone https://github.com/bowenjoseph2014-hash/linux-commands.git
cd linux-commands
```

### Open Locally

```bash
# Open index.html in your default browser
open index.html

# Or directly specify a browser
firefox index.html
# or
chromium index.html
```

---

## 🔗 Useful Resources

- [Arch Linux Wiki](https://wiki.archlinux.org/)
- [Arch Linux Documentation](https://archlinux.org/docs/)
- [Pacman Manual](https://man.archlinux.org/man/pacman.8)
- [Systemd Manual](https://man.archlinux.org/man/systemd.1)
- [GNU Coreutils](https://www.gnu.org/software/coreutils/)

---

## 📂 Repository Structure

```
linux-commands/
├── index.html                    # Interactive website
├── LINUX_TIPS_AND_TRICKS.md     # Markdown guide
└── README.md                     # This file
```

---

## 🤝 Contributing

Feel free to suggest improvements, fixes, or new commands to include:

1. Open an issue with your suggestion
2. Or submit a pull request with improvements

---

## 📄 License

This project is open source and available for everyone to use and learn from.

---

## 🎯 Getting Started with Linux

If you're new to Linux and Arch:

1. Start with the **System Information** section to understand your system
2. Learn **Package Management** to install software
3. Master **File Operations** for everyday tasks
4. Use **Utilities** for advanced text processing
5. Explore **Networking** for internet-related commands

---

## 💡 Pro Tips

### Create Command Aliases
Add to your `~/.bashrc` or `~/.zshrc`:
```bash
alias update='sudo pacman -Syu && yay -Syu'
alias sysinfo='neofetch'
alias ll='ls -lh'
```

### Find Large Files Quickly
```bash
du -sh * | sort -rh | head -10
```

### Monitor System in Real-time
```bash
watch -n 1 'free -h'      # Memory
watch -n 1 'df -h'        # Disk space
```

---

## 🐧 About Arch Linux

Arch Linux is a lightweight and flexible Linux® distribution that tries to keep it simple. The design philosophy encourages its users to understand and participate in the distribution's maintenance.

This guide helps you master essential commands to get the most out of your Arch system!

---

**Last Updated:** 2026  
**Created by:** [@bowenjoseph2014-hash](https://github.com/bowenjoseph2014-hash)

---

Happy Linux hacking! 🚀

**[i see you Bowen.](https://bowenjoseph2014-hash.github.io/linux-commands/me)**
