# notes
Notes for future use

Setting up Django:
1. In the terminal, <code>mkvirtualenv APP_NAME</code>
2. In the virtualenv, <code>pip install django</code>
3. In the virtualenv, <code>pip install psycopg2</code>
4. In the virtualenv, <code>django-admin.py startproject PROJECT_NAME</code>
5. In the virtualenv,  <code>psql postgres</code>
6. In postgres, <code>create database PROJECT_NAME;</code>
7. In the PyCharm project, <code>local_settings.py</code>
8. In <code>local_settings.py</code>
````Python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'writers',
    }
}
````
- 9. 
