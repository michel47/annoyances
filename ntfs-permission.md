# Permission when mounting an NTFS HDD.


Tired of having NTFS disk with 0777 mode (-rwxrwxrwx) for all files and folders...
Here is a solutions : mount is with "permissions" option 

```sh
eval "$(blkid -o export /dev/sda1)"
echo "$LABEL: $DEVNAME, $UUID"
sudo mount /dev/sda1 -t ntfs-3g -o permissions /data/ 
echo "UUID=$UUID /data ntfs-3g rw,nosuid,nodev,relatime,permissions,umask=0022 0 1" | sudo tee -a /etc/fstab 
```


