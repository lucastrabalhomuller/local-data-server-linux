# Step 06 - Connecting to the server on another computer.
On the server computer, you must first know the IP address.
In the Terminal:
```
ip a
```
Now, on the computer you want to access, you must use two commands in the Terminal.

First Command:
```
smbclient -L [Ip Addres] -U%
```
Example:
```
smbclient -L 192.168.0.40 -U%
```

Second Command:
```
smbclient //[Ip Addres]/[Paste]
```
Example:
```
smbclient //192.168.0.40/Work
```
This will prompt the user for their password, then they can enter through the terminal, and then access it via the file manager or terminal.
