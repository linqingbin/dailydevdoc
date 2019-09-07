# Nginx


## Install
Install on Ubuntu
```
sudo apt-get update
sudo apt-get install nginx
```
Version check
```
nginx -v
```

## Admin

### Start server
```shell
sudo /etc/init.d/nginx start
# or
sudo /usr/local/nginx/sbin/nginx
# or
sudo service nginx start
# commands: stop, status, reload
```

### Test config
```
sudo nginx -t
```

### View process
```
ps -ef |grep nginx
```

### View logs
```
ls /var/log/nginx/
```

## Site Config

### Config file location

* `/etc/nginx/nginx.conf`
* `/etc/nginx/sites-enabled/default`

### Keywords

* listen: port to listen
* server_name: host or domin
* root: site root directory
* location: route index


### Config sample

* Static website server
```
server {
    listen 80;
    server_name 10.10.10.10;

    root /{app_root_directory}/;
    index index.html;
}
```

* Dynamic website server
```shell
server {
    listen 80;
    server_name 10.10.10.10;

    location / {
        proxy_pass {dynamic server url};
        # sample: proxy_pass http://127.0.0.1:5500
    }
}
```
		
* Add static resource 
```
location /static/ {
    root /{app_static_directory}/;
}
```

## Problem shooting
### 403 Error

Maybe file permission problem, increase Nginx permsision or set user at nginx.conf, or decrease target files permission.

## Referral
[Nginx Offcial](http://nginx.org/en/docs/beginners_guide.html)
