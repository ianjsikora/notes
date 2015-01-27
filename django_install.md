# notes
Notes for future use

1. First ordered list item
2. Another item
⋅⋅* Unordered sub-list. 
1.  <code>mkvirtualenv APP_NAME</code>
⋅⋅1. Ordered sub-list
4. And another item.


Setting up Django:
1. <code>mkvirtualenv APP_NAME</code>
2. <code>pip install django</code>
3. <code>pip install psycopg2</code>
- 2. 
- 3. 
- 4. <code>django-admin.py startproject PROJECT_NAME</code>
- 5. <code>psql postgres</code>
- 6. <code>create database PROJECT_NAME;</code>
- 7. Open pycham and create <code>local_settings.py</code>
- 8. Add the following to <code>local_settings.py</code>
````Python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'writers',
    }
}
````
- 9. 
