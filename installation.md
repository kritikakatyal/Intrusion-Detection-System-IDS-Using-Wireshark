# Installation Guide

## Prerequisites
Before installing Wireshark, ensure that your system meets the following requirements:

- **Operating System**: Windows, macOS, or Linux (Ubuntu, Debian, CentOS, etc.)
- **Admin Privileges**: Required for installation and packet capture
- **WinPcap/Npcap (Windows only)**: Needed for network packet capturing
- **Libpcap (Linux/macOS)**: Required for packet capturing on Unix-based systems

---

## **Installation on Windows**

### **Step 1: Download Wireshark**
- Visit the official website: [Wireshark Download](https://www.wireshark.org/download.html)
- Download the latest stable version for Windows.

### **Step 2: Install Wireshark**
1. Run the downloaded `.exe` file.
2. Accept the License Agreement.
3. Select the components you want to install (default settings are recommended).
4. **Ensure Npcap is selected** for network packet capturing.
5. Click **Next** and complete the installation.

### **Step 3: Verify Installation**
- Open **Wireshark** and check if network interfaces are listed under `Capture > Options`.
- If no interfaces appear, install/reinstall **Npcap** from [Npcap Download](https://nmap.org/npcap/).

---

## **Installation on Linux (Ubuntu/Debian-based)**

### **Step 1: Update System Packages**
```bash
sudo apt update && sudo apt upgrade -y
```

### **Step 2: Install Wireshark**
```bash
sudo apt install wireshark -y
```

### **Step 3: Grant User Permissions for Packet Capturing**
```bash
sudo usermod -aG wireshark $USER
newgrp wireshark
```

### **Step 4: Verify Installation**
- Run `wireshark` in the terminal or open Wireshark from the applications menu.
- Ensure network interfaces are visible under `Capture > Options`.

---

## **Installation on macOS**

### **Step 1: Install Wireshark Using Homebrew**
```bash
brew install --cask wireshark
```

### **Step 2: Install Capture Permissions (If Required)**
```bash
sudo chown $USER /dev/bpf*
```

### **Step 3: Verify Installation**
- Open Wireshark from the Applications folder.
- Check if network interfaces appear under `Capture > Options`.

---

## 🛠 **Post-Installation Configuration**
- Enable **Promiscuous Mode** in Wireshark (`Edit > Preferences > Capture`)
- Allow network adapter permissions for packet capturing
- Test the installation by capturing live traffic