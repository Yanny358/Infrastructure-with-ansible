## Backup Coverage

There will be backup for 3 services

### 1. Database servers

They are MySQL (stores user data) and InfluxDB (stores system data).

### 2. Ansible repository

 Ansible is backed up at every working release through git.


#### Services which is not backed up:
* Nginx
* AGAMA
* Grafana
* Bind
  
## Recovery Point Objective (RPO)

Backup for MySQL will be done every 24 hours.
Backup for InfluxDB will be done every week (7 days) since it is not as critical as user data.

## Versioning and retention

### MySQL (User data)
Backup once a week - every Sunday, 23:00  UTC, while incremental backups will happen every day at 23:00  UTC

Full backups will be stored for 3 weeks, while only last 7 incremental backups will be stored.


### InfluxDB (System data)
InfluxDB  backups will be made every week at the same time as user data backups - Sunday 23:00  UTC - each backup will be stored for 2 weeks.

### Ansible repository
The repository is powered by git, so every version of the repository is going to be available with no time constraint.

## Usability checks
To ensure the validity of data, on a machine separate from production, MySQL and InfluxDB will be deployed  and their functionality will be verified.

## Restoration criteria
If infrastructure has an error, first the correctness of configuration and operability of services should be verified, after which all the possible errors should go through troubleshooting.

If troubleshooting don't produce any success, restoration from backups will be performed.

## Recovery Time Objective (RTO)
During the restoration, the whole infrastructure can be expected to be redeployed in 1 hour, while data backup restoration can take 1 additional hour.