# Step 2 - Server Control Script

This step creates the main script responsible for controlling the Samba server.

The script checks the current status of the service and automatically starts or stops it.

The script performs the following tasks:

- checks if the Samba service is running
- stops the service if it is active
- starts the service if it is inactive
- sends a desktop notification to the user

---

## Create the control script

Create the server control script:
```
sudo nano /usr/local/bin/server-script
```
Paste the following code into the file:
```
#!/bin/bash
set -e

STATUS="$(systemctl is-active smbd || true)"

if [ "$STATUS" = "active" ]; then
systemctl stop smbd
MSG="Server OFF"
else
systemctl start smbd
MSG="Server ON"
fi

if [ -n "${PKEXEC_UID:-}" ]; then
USERNAME="$(id -nu "$PKEXEC_UID")"
runuser -u "$USERNAME" -- notify-send "Storage Server" "$MSG" || true
fi

exit 0
```

---

## Make the script executable

After saving the file, make it executable:
```
sudo chmod +x /usr/local/bin/server-script
```

---

## How the script works

The script uses `systemctl` to control the Samba service.

Main commands used:

Check server status:
```
systemctl is-active smbd
```

Start the server:
```
systemctl start smbd
```
Stop the server:
```
systemctl stop smbd
```

This script acts as a simple control layer for the storage server.
