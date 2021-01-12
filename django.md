# Setups
To set up django environments, see the following codes
```bash
# Fisrt go to your working directory, use ls to make sure you are within the directory
$ ls 
$ virtualenv -p python3 .
```
### Start virtual environment
``` bash
# Then you need activate your django environment
$ source bin/activate
```

Then you need to install the django environment
```bash
$ pip install django==2.0.7
```

### End virtual environment
```bash
$ deactivate
```

# Creating projects
### Start projects
```bash
# prints a list of available subcommands
$ django-admin

$ mkdir src
$ cd src

# Create projects
$ django-admin startproject trydjangoc .
```

### Access web
```bash
# To access web
python manage.py runserver
```

# References
Reference videos https://www.youtube.com/watch?v=F5mRW0jo-U4
