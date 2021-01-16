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

### Run server
```bash
# Run Server, be sure you are in the src folder
$ python manage.py runserver
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
* Go to folder products
* Go to models.py
* Modify the files and add more class and class attributes

```py
# Create your models here.
class Product(model.Model):
    title       = models.TextField()
    description = models.TextField()
    price       = models.TextField()
```

### Migrate changes
* Go to settings.py and add your own apps
```py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # third party

    # own
    'products',
]
```
* Then in the terminal, do the following
```bash
$ python manage.py makemigrations
$ python manage.py migrate
```

### Notice
Every time when you make changes, you need to make migrations and migrate.

### Change admin register
* Go to admin.py under products
* Add following codes
```py
# Register your models here.
from .models import Product
admin.site.register(Product)
```

# Create Producr Objects in the Python shell
This is another way to create data entries 
```bass
$ python manage.py shell
>>> from products.models import Product
# prints a list of all projects
>>> Product.objects.all()
>>> Product.objects.create(title='New producr 3', description='another one', price='123')
```
* To exit, hit Ctr + D or enter exit()

# More Model Field Types
* Revisit the models.py under produts, many model filed types can be choosen
```py
# Create your models here.
class Product(models.Model):
    title       = models.CharField(max_length=120)  # maxlength is required
    description = models.TextField(blank=True, null=True)
    price       = models.TextField()
    summary     = models.TextField(default="this is cool")
```

### Notice
For more documentation, visit https://docs.djangoproject.com/en/3.1/ref/models/fields/

### More examples
```py
# Create your models here.
class Product(models.Model):
    title       = models.CharField(max_length=120)  # maxlength is required
    description = models.TextField(blank=True, null=True)   # blank means that blank is allowed
    price       = models.TextField()
    summary     = models.TextField(blank=True, null=False)
    featured    = models.BooleanField()
```

# References
Reference videos https://www.youtube.com/watch?v=F5mRW0jo-U4
