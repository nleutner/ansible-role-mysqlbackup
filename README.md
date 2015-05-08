# Ansible Role: MySQLBackup

This Ansible role will setup a db backup user and installs MySQL / MariaDB Backup cron on RHEL/CentOS.

The backup script dumps all MySQL databases to compressed archives using format: "database_%Y%m%d.sql.gz".
By default backups will last for 14 days until removal.
The backup script itself is triggered by cron.daily

## Requirements

MariaDB / MySQL

## Role Variables

Available variables are listed below (see `defaults/main.yml`):

    mysql_use_credentials: tue
    mysql_admin_user: root
    mysql_admin_password: password

MySQL Userdata which will be used for MySQL user creation. If mysql_use_credentials = false, default system credentials will be used (~/.my.cnf).

    mysql_backup_user: backup
    mysql_backup_password: password

MySQL Userdata for the newly created MySQL / MariaDB Backup user.

    mysql_backup_dir: "/data/backups/db/"
    mysql_backup_dir_owner: root
    mysql_backup_dir_group: root
    mysql_backup_permission: "0755"

Backup directory and permission specification, where SQL dumps will be stored.

    mysql_backup_days: 14

Period of time how long dumps will last for.

    mysql_backup_db_ignore: "information_schema"

Databases to ignore during backup, seperated by whitespace

