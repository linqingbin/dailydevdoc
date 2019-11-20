# Python

## Install

### Centos

<https://janikarhunen.fi/how-to-install-python-3-6-1-on-centos-7>

### Ubuntu

Use ppa (Personal Package Archive)

```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.6
```

### Install the necessary libraries

- pip: <https://pip.pypa.io/en/stable/installing/>

- Virtualenv: `pip install virtualenv`

## Admin

### Package install
Pip from image source(Tempoary setting)
```
pip install -I https://pypi.douban.com/simple/
```

Pip from image source(Persistence setting): 

  1. edit $HOME/.pip/pip.conf(Unix) or %HOME%\pip\pip.ini(Windows)
  2. add
```

[global]
timeout = 6000
index-url = http://pypi.douban.com/simple 
trusted-host = pypi.douban.com
```

### Virtualenv

Create virtualenv  with specified version

```
virtualenv env -p /usr/bin/python3.7
```

### Path
Alias python name
```
alias python=python3.7
```

This command can't run use `sudo`, because it is a user level command.

## Code Sample

Get current script location
```python
scriptLocation = os.path.dirname(os.path.realpath(__file__))
```

Get current local datetime
```python
time_str = time.strftime('%Y-%m-%d %H%m%S', time.localtime())
```

Export xlsx without url format
```python
with pd.ExcelWriter(filepath, engine='xlsxwriter', options={'strings_to_urls': False}) as writer:
    df.to_excel(writer, index=False)
```

Save excel-readabel csv with utf-8
```python
resultFilepath = "result.csv"
with open(resultFilepath, mode="w", encoding="utf-8") as f:
    f.write('\ufeff')
    result.to_csv(f, index=False, line_terminator='\n')
```

Sort by a list
```python
[x for _,x in sorted(zip(Y,X))]
```

Quickly understand the information redundancy of pandas dataframe
```python
{x:df[x].duplicated().sum()/df.shape[0] for x in df.columns}
```

Vertical Cmobine two array
```python
np.vstack((x.T,y.T)).T
```

## OOP

### Static method vs class method

Static method can be used before class init.

## Recommend Project File Structure

```
projectName 
	projectName 
		assets
			database.db
		static
			mystyle.css
			rule.js
		templates
			layout.html
		common
			io.py
			setting.py
		componentName
			module1.py
			module2.py
			module3.py
			tools.py
		componentName
			module1.py
			module2.py
			module3.py
			tools.py
		main.py
	tests
		test_main.py
		test_components_module1.py
	run.py
	otherAction.py
readme.md
```

1. Script `main.py` is script for refered, not not for run.
2. Script under every `components` is mutually independant.The common part should saved under common folder.
3. Folder `assets` is Used to save various data.

## Distribution

## Debug

### Microsoft Visual C++ 14.0 is required

visit <https://www.lfd.uci.edu/~gohlke/pythonlibs/#lxml> and download compiled package

### Croniter error when install Django

Version 0.3.26 and 0.3.27 is not exists at croniter, modify version(like 0.3.28) at requirements.txt
