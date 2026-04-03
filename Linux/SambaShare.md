# How to create and share a folder from Linux to Windows

## 🧱 Step 1 – Install Samba on the Linux Remote
```bash
apt update
apt install samba -y
```
## 📁 Step 2 – Create the folder to share
```bash
mkdir -p /mnt/shared
chmod 777 /mnt/shared
```
## Step 3 – Create a Samba user
```bash
smbpasswd -a youruser
```
## ⚙️ Step 4 – Configure the share
```bash
nano /etc/samba/smb.conf
```
Add at the bottom:
```bash
[Shared]
   path = /mnt/shared
   browseable = yes
   read only = no
   guest ok = no
   valid users = youruser
```
## 🔄 Step 5 – Restart Samba
```bash
systemctl restart smbd
```
## 💻 Step 6 – Access from Windows
On Windows PC:
Open File Explorer
In the address bar type:
```bash
\\192.168.1.100\Shared
```
## 🔒 Permissions
If you get access issues:
```bash
chown -R youruser:youruser /mnt/shared
```
## 🔥 Firewall
```bash
ufw allow samba
```

