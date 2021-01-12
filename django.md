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
# Run Server
python manage.py runserver
```

yields the following outputs
```
January 12, 2021 - 23:15:50
Django version 2.0.7, using settings 'trydjango.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
^[[D[12/Jan/2021 23:16:17] "GET / HTTP/1.1" 200 16348
[12/Jan/2021 23:16:17] "GET /static/admin/css/fonts.css HTTP/1.1" 200 423
[12/Jan/2021 23:16:17] "GET /static/admin/fonts/Roboto-Bold-webfont.woff HTTP/1.1" 200 82564
[12/Jan/2021 23:16:17] "GET /static/admin/fonts/Roboto-Regular-webfont.woff HTTP/1.1" 200 80304
[12/Jan/2021 23:16:17] "GET /static/admin/fonts/Roboto-Light-webfont.woff HTTP/1.1" 200 81348
Not Found: /favicon.ico
[12/Jan/2021 23:16:17] "GET /favicon.ico HTTP/1.1" 404 1975
```

* Then you can access the landing page at http://127.0.0.1:8000/, try it in a web browser.
* To go to administration web, visit http://127.0.0.1:8000/admin.

# Create users
```bash
# under src folder/ root files, where manage.py is located
$ python manage.py migrate
$ python manage.py createsuperuser
```

# Start projects
```bash
# You can name whatever names you want
$ python manage.py startapp cart
$ python manage.py startapp products

```


# References
Reference videos https://www.youtube.com/watch?v=F5mRW0jo-U4
