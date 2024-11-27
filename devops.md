### Dev- ops day to day commands

## Docker commands
```
 docker run -d --name sonar -p 9000:9000 sonarqube:lts-community

```

## Ubuntu / linux

### Basic commands
```
mkdir
mv
cp
rm
rm -r
man mv
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
