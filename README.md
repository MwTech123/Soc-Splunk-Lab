# SOC-Splunk-Lab –Splunk SIEM Deployment & SSH Brute Force Detection

## Overview
This project demonstrates the deployment and configuration of a Splunk SIEM environment in a virtual lab. The objective was to gain hands-on experience with:

## Lab Environment

| Component | Configuration |
|----------|--------------|
| Host OS | Windows 11 |
| Hypervisor | Oracle VirtualBox |
| Guest OS | Ubuntu Server |
| SIEM | Splunk Enterprise |
| Network | NAT with Port Forwarding (Port 8000) |

---

## Installation Steps
1. Install Ubuntu Server:

    Deployed Ubuntu Server VM using VirtualBox.

2. Install VirtualBox Guest Additions:

    Enabled clipboard sharing and shared folders.

3. Install Splunk Downloaded and installed the Splunk .deb package:

    sudo dpkg -i splunk-*.deb

4. Start Splunk:
   
    sudo /opt/splunk/bin/splunk start --accept-license

5. Enable Splunk at Boot:

    sudo /opt/splunk/bin/splunk enable boot-start -user socadmin


## Access
Splunk Web Interface:
http://localhost:8000


## Detection Use Case: SSH Brute Force
## SPL Query

index=* "Failed password"

| stats count by src_ip

| where count > 5

This detection identifies repeated failed SSH login attempts from the same source IP.

## Alert Configuration

- Name: SSH Brute Force Detection
- Type: Scheduled
- Trigger: Number of results > 0
- Action: Alert notification

## Skills Demonstrated 
- SIEM Deployment (Splunk)
- Log ingestion and analysis
- SPL query development
- Security alert configuration
- VirtualBox lab setup
- Linux administration
- Basic SOC detection workflow

## Screenshots

