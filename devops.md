### Dev- ops day to day commands

## Docker commands
```
 docker run -d --name sonar -p 9000:9000 sonarqube:lts-community

```

## Ubuntu / linux

https://medium.com/@vinodhakumara2681997/cheatsheet-linux-commands-for-devops-80be32b88656

### Basic commands

#### File and Directory
ls
cd
pwd
mkdir
rm
cp
mv
find
chmod
chown
chgrp


#### Text manipulation
cat
grep
head
tail
less
sed
awk


#### Process Management
ps
top
kill
systemctl
service
df
du
free
uptime


#### Networking

ping
curl
ssh
scp
netstat
ifconfig
iptables

```
mkdir
mv
cp
rm
rm -r
man mv
ssh -i <key file> <uname>@<ipaddresses>
history
pwd
whoami
sudo su - changes the user to su
docker --version or docker
which docker - returns the location of the folder
which git

date

vi - editor

:wq - Save and Exit
:qa! - to exit without the savings

ping google.com
ping amazon.com
ip addr
nslookup google.com - return the server address

curl <url>

wget - to download the package


## Fedora / Amazon Linux
sudo apt update && sudo apt upgrade
sudo yum install docker (Fedora)
sudo apt install docker (Ubuntu)

```

### Ubuntu increasing the root volume size and expanding the partition
```
df -T /

sudo apt update

sudo apt install cloud-guest-utils

sudo growpart /dev/xvda 1

sudo resize2fs /dev/xvda1

 lsblk
```



## Mysql

### To create a backup of mysql

```
mysqldump -u root -p dbname > dbname-date.sql
```

### To restore a backup

```
mysql -h slotmastersbattle.c46zok4nn5q6.us-east-1.rds.amazonaws.com -u username -p dbname < sqlfilename

```
