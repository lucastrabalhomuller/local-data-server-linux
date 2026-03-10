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
