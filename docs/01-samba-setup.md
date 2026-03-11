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
Place the configuration at the end of the file.

Example configuration:
```
[data]

path = /mnt/storage
browseable = yes
read only = no
guest ok = no
```
add a user to samba:
```
sudo smbpasswd -a user
```
He will ask for a password.
 
## Restart the service
```
sudo systemctl restart smbd
```

This step creates the base file sharing server.
