# stat
* https://www.tecmint.com/debugfs-command-show-file-creation-time-in-linux/
## with ext4
```
ls -lc filename

ls -i filename 
stat -c %i filename 
debugfs -R 'stat <inode_number>' device
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
