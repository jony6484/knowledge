## 1. Basic One-Way Sync Script 

This syncs a folder from **PC1 → PC2**
### Example

Sync:

```
/home/jon/files
```

to:
```
/home/jon/files
```

### PC1

```bash
rsync -avz /home/jon/files/ jon@192.168.1.50:/home/jon/files/
```


```bash
-a archive mode  
-v verbose  
-z compression
```
Trailing `/` means _copy contents_, not the folder itself.

### Create a Sync Script
```bash
nano sync_folder.sh
```
```bash
#!/bin/bash  
  
SOURCE="/home/jon/files/"  
DEST="jon@192.168.1.50:/home/jon/files/"  
  
rsync -avz --delete "$SOURCE" "$DEST"
```

`--delete` removes files on destination that were deleted locally (true mirror).

Make exec:
```bash
chmod +x sync_folder.sh
./sync_folder.sh
```

### Auto Sync Every X Minutes
```bash
crontab -e
```

Example every 5 minutes:

```bash
*/5 * * * * /home/jon/sync_folder.sh
```

## 2.  If You Want **Two-Way Sync**

```bash
sudo apt install unison

unison /home/jon/files ssh://jon@192.168.1.50//home/jon/files
```
