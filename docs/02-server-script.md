# Step 2 - Create the Storage Server

This step creates the storage server that will be shared across the local network.

The server uses **Samba** to expose a directory that other devices can access.

---

## Variables used in this guide

The paths used in this guide are only examples.

You can choose any directory that exists on your system.

Variables used:

SERVER_DIR → directory that will store the shared files  
SERVER_USER → user allowed to access the server  
SHARE_NAME → name of the Samba share

Example used in this guide:

SERVER_DIR = /mnt/storage  
SERVER_USER = storage  
SHARE_NAME = data

You can replace these values with your own paths and names.

## Create the server directory

Create the directory that will store the shared files.

Example:
```
sudo mkdir -p /mnt/storage
```
Set permissions:
```
sudo chmod 755 /mnt/storage
```
## Create the server setup script

Create a script that will configure the storage server automatically.

```
sudo nano /usr/local/bin/server-setup
```

Paste the following code:

```bash
#!/bin/bash

SERVER_DIR="/mnt/storage"
SERVER_USER="storage"
SHARE_NAME="data"

# Create directory
mkdir -p "$SERVER_DIR"
chmod 755 "$SERVER_DIR"

# Create server user
id "$SERVER_USER" &>/dev/null || useradd -M -s /usr/sbin/nologin "$SERVER_USER"

# Configure Samba share
if ! grep -qF "[$SHARE_NAME]" /etc/samba/smb.conf; then
echo "
[$SHARE_NAME]
path = $SERVER_DIR
browseable = yes
read only = no
guest ok = no
" >> /etc/samba/smb.conf
fi

systemctl restart smbd

echo "Storage server created successfully."
```

Make the script executable:

```
sudo chmod +x /usr/local/bin/server-setup
```
