## The regular way:
```bash
sudo usermod -aG docker $USER
```

## The hack way:
```bash
sudo vigr
OR
sudo vigr -s
```

add user to ==sudo== or ==docker== if needed (onetime root needed)
```bash
docker:x:996:jonaf
sudo:x:27:jonaf,ubadmin
```



