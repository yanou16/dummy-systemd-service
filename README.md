# Dummy Systemd Service

This repository contains a simple **dummy systemd service** created to demonstrate how to manage long-running background scripts on a Linux VM. The project was implemented and tested on a **Google Cloud Compute Engine VM**.
https://roadmap.sh/projects/dummy-systemd-service
<img width="996" height="337" alt="image" src="https://github.com/user-attachments/assets/2118d2f9-efcc-4c8e-b2d2-9ee3388ed802" />

## Project Overview

The goal of this project is to practice:

- Writing a script that runs continuously in the background.
- Creating a **systemd service** to manage the script.
- Using `systemctl` commands to start, stop, enable, disable, and monitor the service.
- Viewing logs with `journalctl`.
- Ensuring the service restarts automatically if it fails.

The dummy service logs a message to a file every 10 seconds, simulating a simple application running in the background.

---

## Files

- `dummy.sh` — Bash script that runs indefinitely and logs a message every 10 seconds.  
- `dummy.service` — Systemd service configuration file for `dummy.sh`.

---

## Setup Instructions

### 1. Copy the files to the VM
```bash
sudo cp dummy.sh /usr/local/bin/dummy.sh
sudo cp dummy.service /etc/systemd/system/dummy.service
````

2. Make the script executable
```bash
sudo chmod +x /usr/local/bin/dummy.sh

````

3. Reload systemd and enable the service
```bash
sudo systemctl daemon-reload
sudo systemctl start dummy       # Start immediately
sudo systemctl enable dummy      # Start automatically on boot

````
4. Check the status and logs
```bash
sudo systemctl status dummy      # Check if running
sudo journalctl -u dummy -f      # Tail logs live

````
5. Manage the service
```bash
sudo systemctl stop dummy        # Stop the service
sudo systemctl disable dummy     # Disable autostart on boot

````

Google Cloud Setup

This project was performed on a Google Cloud VM using the SSH terminal. Steps included:

Creating a Compute Engine VM.

Connecting via SSH.

Using nano to create the dummy.sh and dummy.service files.

Managing the service directly from the VM terminal.

Rayane Louzazna
GitHub: yanou16


