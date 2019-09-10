# Python

## Install

### Centos

[https://janikarhunen.fi/how-to-install-python-3-6-1-on-centos-7](https://janikarhunen.fi/how-to-install-python-3-6-1-on-centos-7)
    
### Ubuntu

Use ppa (Personal Package Archive)
```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.6
```
### Install the necessary libraries

* pip: [https://pip.pypa.io/en/stable/installing/](https://pip.pypa.io/en/stable/installing/)

* Virtualenv: `pip install virtualenv`


## Admin




### Alias python name
```
alias python=python3.7
```
This command can't run use `sudo`, because it is a user level command. 
	

### Pip from image source
Tempoary setting
```    
pip install -I https://pypi.douban.com/simple/
```
Persistence setting: edit $HOME/.pip/pip.conf(Unix) or %HOME%\pip\pip.ini(Windows)
```
[global]
timeout = 6000
index-url = http://pypi.douban.com/simple 
trusted-host = pypi.douban.com
```

### Create Virtualenv with specified version
```
virtualenv env -p /usr/bin/python3.7
```

## Code Sample

### Get current script location
```
scriptLocation = os.path.dirname(os.path.realpath(__file__))
```
	

### Get current local datetime
```
time_str = time.strftime('%Y-%m-%d %H%m%S', time.localtime())
```

### Export xlsx without url format
```
with pd.ExcelWriter(filepath, engine='xlsxwriter', options={'strings_to_urls': False}) as writer:
    df.to_excel(writer, index=False)
```

### Save excel-readabel csv with utf-9
```
with open("food.csv", "w", encoding="utf-8") as f:
    f.write('\ufeff')
    df.to_csv(f, encoding="utf-8", index=False)
```

### Sort by a list
```
[x for _,x in sorted(zip(Y,X))]
```

### Quickly understand the information redundancy of a list
	{x:df[x].duplicated().sum()/df.shape[0] for x in df.columns}

### Vertical Cmobine two array 
```
np.vstack((x.T,y.T)).T
```
## OOP
	
### Static method vs class method

Static method can be used before class init.

## Data Science

## Distribution

## Debug

### Microsoft Visual C++ 14.0 is required
visit [https://www.lfd.uci.edu/~gohlke/pythonlibs/#lxml](https://www.lfd.uci.edu/~gohlke/pythonlibs/#lxml) and download compiled package


### Croniter error when install Django
Version 0.3.26 and 0.3.27 is not exists at croniter, modify version(like 0.3.28) at requirements.txt