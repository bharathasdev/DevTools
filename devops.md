### Dev- ops day to day commands

## Ubuntu / linus

### Ubuntu increasing the root volume size and expanding the partition
```
df -T /

sudo apt update

sudo apt install cloud-guest-utils

sudo growpart /dev/xvda 1

sudo resize2fs /dev/xvda1

 lsblk
```
