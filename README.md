# Local Data Storage Server (Linux)

A lightweight local storage server for Linux using **Samba**, controlled by **Bash scripts** and **simple graphical applications**.

This project provides an easy way to manage a personal file server on a local network without requiring complex system administration tools.

The server can be **started, stopped, and monitored through desktop applications**, making it suitable for personal storage and data access across devices on the same network.

---

## Overview

This project implements a simple local data server using:

- **Samba** for network file sharing
- **systemd** for service management
- **Bash scripts** for automation
- **Zenity** for graphical dialogs and status windows

The system allows users to control the server through two graphical utilities:

1. **Server Control**
   - Starts or stops the Samba service.
   - Displays the current server status.

2. **Server Status**
   - Checks if the server is active.
   - Displays a simple graphical status message.

These utilities simplify server control for users who prefer graphical tools instead of terminal commands.

---

## Features

- Simple **local storage server**
- **Start/stop server with one click**
- **Graphical status monitoring**
- Uses standard Linux components
- Lightweight and easy to maintain
- No complex server frameworks required

---

## Requirements

The following packages are required:
Install them on Debian/Ubuntu based systems:

---
## Setup Instructions

This project is organized so that the configuration process can be understood step by step.

To correctly set up the server, read the files in this repository **in order**, starting from the basic configuration and moving toward the graphical control scripts.

Each file contains comments explaining its role in the system.

Recommended reading order:

1. Server configuration (Samba configuration)
2. Service control scripts
3. Graphical control scripts
4. Desktop application files

Following the files in this order helps understand how the server is configured, how the service is controlled, and how the graphical utilities interact with the system.

