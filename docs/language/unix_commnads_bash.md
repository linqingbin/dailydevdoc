# Unix Commands & Bash

## Unix Commands

### Samples

Remove files under folder

```
rm -rf /path/to/directory/*
```

Count the number of files

```
ls wc -l
```

IP test

```
curl ifconfig.me
```

Search process by keyword

```
ps -ef | grep {keyword}
```

Search file by keyword

```
ls {folder path} | grep {keyword}
```

Search log info by keyword

```
cat {log file path} | grep {keyword}
```

### Libraries

- Memory view: atop
- Kill process by keyword: pkill -f supervisord

### Referral

[Basic UNIX commands](http://mally.stanford.edu/~sr/computing/basic-unix.html)

## Bash

[Bash scripting cheatsheet](https://devhints.io/bash)

## User management

### Referral

- [Ubuntu File Permissions](https://help.ubuntu.com/community/FilePermissions)
- [Ubuntu User Management](https://help.ubuntu.com/lts/serverguide/user-management.html)

### Useful commands

- Modify permission of file: `chmod u+x filePath`
- Add user to group: `sudo adduser username groupname`
- Check all user: `cat /etc/passwd`
- Change all file permission under directory: `chown -R username:group directory`

## Crontab

### Config crontab

* User level: `crontab -e`
* Global level: `sudo nano /etc/crontab`

[referr link](https://stackoverflow.com/questions/22203120/cronjob-entry-in-crontab-e-vs-etc-crontab-which-one-is-better)

Sample:
```
*/1 * * * *     root    /root/projects/anirec/start_anirec.sh
```

### Check crontab log
	centos
		sudo tail /var/log/cron
	ubuntu
        grep CRON /var/log/syslog