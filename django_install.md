# Setting up Django

* In the terminal, <code>mkvirtualenv APP_NAME</code>
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
        'NAME': 'writers',
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
* In Pycharm, 
⋅⋅* Click on PyCharm -> Preferences -> Project Interpreter
⋅⋅* Click on the Gear Icon -> Add Local
⋅⋅* Go to your home directory -> .virtualenvs -> writers -> bin -> file named <code>Python</code>

