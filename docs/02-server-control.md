# Step 2 - Server Control Script

This project uses a Bash script to control the Samba server.

The script can:

- check if the service is running
- start the service
- stop the service
- notify the desktop user

Core command used:
```
systemctl is-active smbd
```
Start server:
```
systemctl start smbd
```
Stop server:
```
systemctl stop smbd
```
These commands are wrapped inside the control script.
