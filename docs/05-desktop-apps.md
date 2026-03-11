# Step 5 - Desktop Applications

This step creates desktop applications that allow the user to control the server from the system menu.

These applications call the server scripts created in the previous steps.

---

## Application location

Desktop application files are stored in:
```
/usr/share/applications
```

---

# Server Control App

Create the server control application:
```
sudo nano /usr/share/applications/server-control.desktop
```

Paste:
```
[Desktop Entry]
Name=Storage Server Control
Exec=/usr/local/bin/server-status
Icon=network-server
Terminal=false
Type=Application
Categories=System;

```

Save the file.

---

# Server Status App
Create a command for the status:
```
sudo nano /usr/local/bin/server-status
```
Paste:
```
#!/bin/bash

STATUS="$(/usr/bin/systemctl is-active smbd 2>/dev/null || true)"

if [ "$STATUS" = "active" ]; then
  /usr/bin/zenity --info \
  --title="Storage Server" \
  --text="🟢 Server ACTIVE"
else
  /usr/bin/zenity --warning \
  --title="Storage Server" \
  --text="🔴 Server STOPPED"
fi
```

Create the server status application:
```
sudo nano /usr/share/applications/server-status.desktop
```

Paste:
```
[Desktop Entry]
Name=Storage Server Status
Exec=sh -c /usr/local/bin/server-status
Icon=network-workgroup
Terminal=false
Type=Application
Categories=System;
```

Save the file.

---

## What these apps do

These applications allow the user to control the server directly from the desktop environment.

The applications will appear in the system menu.

