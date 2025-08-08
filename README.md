# Firewall Rule Testing – Windows & Linux

## Overview
This task demonstrates configuring and testing firewall rules on both Windows and Linux to control inbound WSMAN traffic and SSH traffic.

## Tasks Performed
- **Windows**: Used Windows Defender Firewall to block inbound WSMAN traffic (port 5985) and verified the block using Kali Linux.
- **Linux**: Used UFW (Netfilter) to block inbound SSH traffic (port 22) and verified the block using Windows.

## Tools Used
- **Windows Defender Firewall** – GUI and command-line firewall management for Windows.
- **UFW** – Simplified interface to the Netfilter firewall in Linux.

---

## Windows – Firewall Rule Setup (GUI)
1. Open **Control Panel** → **Windows Defender Firewall**.
2. Click **Advanced settings** on the left panel.
3. In the **Windows Firewall with Advanced Security** window, select **Inbound Rules**.
4. Click **New Rule…**.
5. Choose **Port**, then click **Next**.
6. Select **TCP** and enter **5985** (WSMAN default port).
7. Choose **Block the connection** and click **Next**.
8. Select **Domain**, **Private**, and **Public** as needed, then click **Next**.
9. Give the rule a name (e.g., `Block WSMAN 5985`) and click **Finish**.
10. Test by attempting to connect from Kali Linux.

---

## Linux – Setup SSH Service
```bash
sudo systemctl start ssh       # Start SSH service
sudo systemctl enable ssh      # Enable SSH service at boot
sudo systemctl status ssh      # Check SSH service status
```
## Linux – Setup SSH Service
```bash
sudo ufw status                # Check firewall status
sudo ufw enable                # Enable the firewall
sudo ufw allow 22/tcp          # Allow incoming SSH traffic
sudo ufw deny 22/tcp           # Block incoming SSH traffic
```
## Final Result
- Both Wsman and ssh  connection attempts were successfully blocked in both directions, conforming firewall effectiveness.

