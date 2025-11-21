# backapick
Simple bacup script

---

# Find empty backup archives and log files
```console
find . -type f -name "*_backup.log.bz2" -size -50c -exec bash -c 'if [[ "$(bzcat {})" = "" ]]; then echo {}; fi' \;
find . -type f -name "*_backup.log" -size 0c -exec bash -c 'if [[ "$(cat {})" = "" ]]; then echo {}; fi' \;

find . -type f -name "*_backup.tar.bz2" -size -100c -exec bash -c 'if [[ "$(tar --list -f {} 2>/dev/null)" = "" ]]; then echo {}; fi' \;
find . -type f -name "*_backup.tar" -size -20480c -exec bash -c 'if [[ "$(tar --list -f {} 2>/dev/null)" = "" ]]; then echo {}; fi' \;
```
# Remove empty backup archives and log files
```console
find . -type f -name "*_backup.log.bz2" -size -50c -exec bash -c 'if [[ "$(bzcat {})" = "" ]]; then echo {}; rm {}; fi' \;
find . -type f -name "*_backup.log" -size 0c -exec bash -c 'if [[ "$(cat {})" = "" ]]; then echo {}; rm {}; fi' \;

find . -type f -name "*_backup.tar.bz2" -size -100c -exec bash -c 'if [[ "$(tar --list -f {} 2>/dev/null)" = "" ]]; then echo {}; rm {}; fi' \;
find . -type f -name "*_backup.tar" -size -20480c -exec bash -c 'if [[ "$(tar --list -f {} 2>/dev/null)" = "" ]]; then echo {}; rm {}; fi' \;

```
# lbunzip2 all .bz2 files
```console
find . -type f -name "*.bz2" -exec bash -c 'echo -n "{}... "; lbunzip2 {}; echo "done"' \;
```

# lbzip2 all xxx files
```console
find . -type f -name "*_backup.log" -exec bash -c 'echo -n "{}... "; lbzip2 {}; echo "done"' \;
find . -type f -name "*_backup.tar" -exec bash -c 'echo -n "{}... "; lbzip2 {}; echo "done"' \;
```
