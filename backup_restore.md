## MySQL Restoring


### 1. MySQL dumps
Are done by cron tabs located in /etc/cron.d/mysql-backup
After dump is done you can delete item in agama web app to check backup restoration after.

### 2
To add data to server -> sudo -u backup  duplicity --no-encryption full /home/backup/mysql/ rsync://Yanny358@backup.iptv.cs//home/Yanny358/

### 3 
To add data difference to server -> sudo -u backup  duplicity --no-encryption incremental /home/backup/mysql/ rsync://Yanny358@backup.iptv.cs//home/Yanny358/

### 4
To download data -> sudo -u backup duplicity --no-encryption restore  rsync://Yanny358@backup.iptv.cs//home/Yanny358/ /home/backup/restore

### 5
To restore data -> (run as root) mysql agama < /home/backup/restore/agama.sql 
Now items will be back after you refresh agama web page.

## InfluxDB Restoring

### 1. InfluxDB dumps
Are done by cron tabs located in /etc/cron.d/influxdb-backup

### 2
To add data to server -> sudo -u backup  duplicity --no-encryption full /home/backup/influxdb/ rsync://Yanny358@backup.iptv.cs//home/Yanny358/

### 3
To download data -> sudo -u backup duplicity --no-encryption restore  rsync://Yanny358@backup.iptv.cs//home/Yanny358/ /home/backup/restore

### 4 To restore data
Run as root 
* service telegraf stop
* influx -execute 'DROP DATABASE telegraf'
* influxd restore -portable -database telegraf /home/backup/influxdb

Output should be something similiar to this -> 2021/11/11 14:46:27 Restoring shard 3 live from backup 20211111T133034Z.s3.tar.gz

