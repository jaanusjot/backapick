# backapick
Simple bacup script

---

# Find empty incremental backups
```console
find . -type f -name "*incremental_backup.tar*" -exec bash -c 'if [ "$(tar --list -f {} 2>/dev/null)" = "" ]; then echo {}; fi' \;
```
# Remove empty incremental bakups
```console
find . -type f -name "*incremental_backup.tar*" -exec bash -c 'if [ "$(tar --list -f {} 2>/dev/null)" = "" ]; then rm {}; echo {}; fi' \;
```

---

# Find empty uncompressed log files
```console
find . -type f -name "*incremental_backup.log" -exec bash -c 'if [ "$(cat {})" = "" ]; then echo {}; fi' \;
```
# Delete empty uncompressed log files
```console
find . -type f -name "*incremental_backup.log" -exec bash -c 'if [ "$(cat {})" = "" ]; then rm {}; echo {}; fi' \;
```

---

# Find empty compressed log files
```shell
find . -type f -name "*incremental_backup.log.bz2" -exec bash -c 'if [ "$(bzcat {})" = "" ]; then echo {}; fi' \;
```
# Delete empty compressed log files
```console
find . -type f -name "*incremental_backup.log.bz2" -exec bash -c 'if [ "$(bzcat {})" = "" ]; then rm {}; echo {}; fi' \;
```

---

# bunzip2 all .bz2 files
```console
find . -type f -name "*.bz2" -exec bash -c 'lbunzip2 {}; echo {}' \;
```
