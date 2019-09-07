# Supervisor

## Install
```shell
pip install supervisor
```

## Admin

### Start 
```shell
# In config directory
cd /etc/supervisor/
supervisord
```

If start multiple supervisor task accidently, kill process find in `ps -ef`.
	
	
## Command tool
```shell
# run
supervisorctl
# shutdown
supervisorctl shutdown
```
	
## Config

File location: /etc/supervisor/supervisord.conf

Config Sample
```shell
[supervisord]

[supervisorctl]

[program:foo]
command=/root/projects/servertest/env/bin/python /root/projects/servertest/manage.py runserver
```

## Debug
### Execute faild

    Permission related
    