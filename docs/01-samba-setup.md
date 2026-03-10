# Step 1 - Samba Configuration

The storage server is based on Samba, which allows file sharing across the local network.

## Install Samba
```
sudo apt install samba
```

## Edit the Samba configuration
```
sudo nano /etc/samba/smb.conf
```

Example configuration:
```
[data]

path = /mnt/storage
browseable = yes
read only = no
guest ok = no
```
 
## Restart the service
```
sudo systemctl restart smbd
```

This step creates the base file sharing server.
