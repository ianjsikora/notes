## Setting up Django Project

* In the terminal, <code>mkvirtualenv PROJECT_NAME</code>
* In the virtualenv, <code>pip install django</code>
* In the virtualenv, <code>pip install psycopg2</code>
* In the virtualenv, <code>django-admin.py startproject PROJECT_NAME</code>
* If the DB isn't running, in the virtualenv, run <code>postgres -D /usr/local/var/postgres</code>
* In the virtualenv,  <code>psql postgres</code>
* In postgres, open <code>create database PROJECT_NAME;</code>
* In PyCharm, create the file <code>local_settings.py</code>
* In <code>local_settings.py</code> paste
````Python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'PROJECT_NAME',
    }
}
````
* In <code>settings.py</code>, under the <code>DATABASES</code> section paster
````Python
try:
    from local_settings import *
except ImportError:
    pass
````
* In Pycharm, click on PyCharm -> Preferences -> Project Interpreter -> Gear Icon -> Add Local. Go to your home directory -> .virtualenvs -> PROJECT_NAME -> bin -> <code>python</code>

## Setting up Django App
* In virtualenv, <code>cd PROJECT_NAME</code> (same level as <code> manage.py</code>
* In virtualenv, <code>python manage.py startapp APP_NAME</code>
* In PyCharm project, open <code>settings.py</code> and in <code>INSTALLED_APPS</code> add <code>'APP_NAME'</code>

### Creating Data Model
* In <code>models.py</code>, under <code>from django.db import models</code> paste
````Python
class TABLE_NAME(models.Model):
    variable1 = models.CharField(max_length=120)
    variable2 = models.CharField(max_length=40, null=True)

    def __unicode__(self):
        return u"{}".format(self.variable1)
````
* In virtualenv, <code>python manage.py makemigrations</code>
* In virtualenv, <code>python manage.py migrate</code>

# Setting up Django Admin
* In virtualenv, <code>python manage.py createsuperuser</code>
* In <code>Username: </code>, enter an admin_name
* In <code>Email address: </code>, enter admin_email
* In <code>Password: </code>, enter a password
* In PyCharm, check <code>settings.py</code> under <code>INSTALLED_APPS</code> and make sure you see <code>'django.contrib.admin',</code>
* In PyCharm, open <code>admin.py</code> and paste 
````Python
from django.contrib import admin
from your_app.models import TABLE_NAME

class TABLE_NAMEAdmin(admin.ModelAdmin):
    fields = ['variable1','variable2']

admin.site.register(TABLE_NAME, TABLE_NAMEAdmin)
````
