# stat

## with ext4
```
ls -lc filename
stat -c %i filename 
debugfs -R 'stat <inode_number>' device
debugfs -R 'stat /boot/onext4.txt' /dev/sda1
```

