# stat

## with ext4
```
ls -lc filename
stat -c %i filename 
debugfs -R 'stat <inode_number>' device
debugfs -R 'stat /boot/onext4.txt' /dev/sda1
```

cat filedate.sh
```
#!/bin/bash -x

function usage(){
  echo -n "$0 <file>"
}

if [ $# -lt 1 ];then
  usage
  exit 20
fi

MYFILE="$1"
DEVICE=`df -h $MYFILE | tail -n 1| awk '{print $1}'`
INODE=`ls -i $MYFILE|awk '{print $1}'`
debugfs -R "stat <${INODE}>"  $DEVICE
```
