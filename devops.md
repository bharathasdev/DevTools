### Dev- ops day to day commands

## Docker commands
```
 docker run -d --name sonar -p 9000:9000 sonarqube:lts-community

```

## Ubuntu / linux

### Ubuntu increasing the root volume size and expanding the partition
```
df -T /

sudo apt update

sudo apt install cloud-guest-utils

sudo growpart /dev/xvda 1

sudo resize2fs /dev/xvda1

 lsblk
```
