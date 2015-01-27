# notes
Notes for future use

Setting up Django:
- [ ] <code>mkvirtualenv APP_NAME</code>
- [ ] <code>pip install django</code>
- [ ] <code>pip install psycopg2</code>
- [ ] <code>django-admin.py startproject PROJECT_NAME</code>
- [ ] <code>psql postgres</code>
- [ ] <code>create database PROJECT_NAME;</code>
- [ ] Open pycham and create <code>local_settings.py</code>
- [ ] Add the following to <code>local_settings.py</code>
````Python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'writers',
    }
}
````
- [ ] 
