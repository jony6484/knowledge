```bash
#!/bin/bash
# backup_mount.sh
# Manually mount SSHFS shared folder for backup

# CONFIGURATION
SERVER="d-p-jonafl-l-rf"
USER="jonaf"        # replace with your server username
REMOTE_PATH="/srv/shared_folder"
LOCAL_PATH="$HOME/shared_folder"

# Create local mount point if it doesn't exist
mkdir -p "$LOCAL_PATH"

# Check if already mounted
if mount | grep -q "$LOCAL_PATH"; then
    echo "✅ Already mounted at $LOCAL_PATH"
    exit 0
fi

# Mount via SSHFS
echo "🔗 Mounting $REMOTE_PATH from $USER@$SERVER to $LOCAL_PATH..."
sshfs "$USER@$SERVER:$REMOTE_PATH" "$LOCAL_PATH" -o allow_other,reconnect

# Check if mount succeeded
if mount | grep -q "$LOCAL_PATH"; then
    echo "✅ Mount successful!"
else
    echo "❌ Mount failed!"
fi
```

---
