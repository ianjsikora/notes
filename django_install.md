# Setting up Django Project

* In the terminal, <code>mkvirtualenv PROJECT_NAME</code>
* In the virtualenv, <code>pip install django</code>
* In the virtualenv, <code>pip install psycopg2</code>
* In the virtualenv, <code>django-admin.py startproject PROJECT_NAME</code>
* In the virtualenv,  <code>psql postgres</code>
* In postgres, <code>create database PROJECT_NAME;</code>
* In the PyCharm project, <code>local_settings.py</code>
* In <code>local_settings.py</code>
````Python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'PROJECT_NAME',
    }
}
````
* In <code>settings.py</code>, under the <code>DATABASES</code> section
````Python
try:
    from local_settings import *
except ImportError:
    pass
````
* In Pycharm, click on PyCharm -> Preferences -> Project Interpreter -> Gear Icon -> Add Local. Go to your home directory -> .virtualenvs -> PROJECT_NAME -> bin -> <code>python</code>

# Setting up Django App
* In virtualenv, <code>cd PROJECT_NAME</code>
* In virtualenv, <code>python manage.py startapp APP_NAME</code>
* In PyCharm projecrt, open <code>settings.py</code> and in <code>INSTALLED_APPS</code> add <code>'APP_NAME'</code>
* Something

