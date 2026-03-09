
---
## 1. Create a `.desktop` file

These are stored in:

```bash
~/.local/share/applications/
```

Create one:

```bash
nano ~/.local/share/applications/myapp.desktop
```

Example content:

```bash
[Desktop Entry]  
Name=My App  
Comment=My custom executable  
Exec=/home/jonathan/path/to/my/program  
Icon=/home/jonathan/path/to/icon.png  
Terminal=false  
Type=Application  
Categories=Utility;
```

Important fields:

- **Name** → what appears in the menu
- **Exec** → full path to the executable
- **Icon** → optional but recommended
- **Terminal=true** if it runs in a terminal
---
## 2. Make the launcher executable

```bash
chmod +x ~/.local/share/applications/myapp.desktop
```
---
## 3. Refresh the applications list

Usually it appears automatically, but if not:
```bash
update-desktop-database ~/.local/share/applications
```

Then press **Super (Windows key)** and search for the app name.

---
## 4. Optional: Put it on the Desktop

Copy it:

```bash
cp ~/.local/share/applications/myapp.desktop ~/Desktop/  
chmod +x ~/Desktop/myapp.desktop
```

Right-click → **Allow Launching** if Ubuntu asks.