## Setting up Server Instance and Config
* Setup AWS server and download pem file (first ubunt
* In the terminal, <code>mv ~/Downloads/PEM_FILE.pem ~/.ssh/</code>
* In the terminal, <code>cd ~/.ssh</code>
* In the terminal, <code>chmod 400 PEM_FILE.pem</code>
* In the terminal, <code>open ~/.ssh/config</code> and add in the Amazon IP

## Installing Software on the Server
* In the terminal, <code>ssh PEM_FILE</code>
* In the server (terminal),  <code>sudo apt-get update</code>
* In the server (terminal),  <code>sudo apt-get upgrade</code>
* In the server (terminal),  <code>sudo apt-get install nginx</code>
* In the server (terminal),  <code>sudo apt-get install git</code>
* If a simple HTTP page, then:
 * In the server (terminal),  <code>cd /etc/nginx/sites-enabled/</code>
 * In the server (terminal),  <code>sudo mv default PROJECT_NAME.conf</code>
 * In the server (terminal),  <code>sudo nano PROJECT_NAME.conf</code>
 * Edit the location of the website from <code>root /usr/share/nginx/html;</code> to <code>root /home/ubuntu/PROJECT_NAME;</code>
 * In the server (terminal),  <code>sudo service nginx restart</code>

## Getting Website Files from Github
* In the server (terminal),  <code>ssh-keygen -t rsa</code>
* In the server (terminal),  <code>cat ~/.ssh/id_rsa.pub</code> and paste the key in Github
* In the server (terminal),  <code>cd ~/</code>
* In the server (terminal),  <code>git clone GITHUB_REPO</code>

## Make Virtualenv
* In the server (terminal),  <code>sudo apt-get install python-pip python-dev build-essential</code>
* In the server (terminal),  <code>sudo pip install pip --upgrade</code>
* In the server (terminal),  <code>sudo pip install virtualenv --upgrade</code>
* In the server (terminal),  <code>sudo pip install virtualenvwrapper</code>
* In the server (terminal),  <code>mkdir ~/.virtualenvs</code>
* In the server (terminal),  <code>emacs ~/.bashrc</code>
* In the server (terminal),  <code>export WORKON_HOME=~/.virtualenvs</code>
* In the server (terminal),  <code>source ~/.bashrc</code>
* In the server (terminal),  <code>mkvirtualenv PROJECT_NAME</code>

## Setup Postgres
* In the server (terminal),  <code>sudo adduser PROJECT_NAME</code>
* In the server (terminal),  <code>sudo apt-get install postgresql postgresql-contrib libpq-dev</code>
* In the server (terminal),  <code>createuser --interactive</code> and name the user PROJECT_NAME and remember 'myawesomepassword'
* In the server (terminal),  <code>createdb PROJECT_NAME</code> and Cmd-D back to user:ubuntu
* In the server (terminal),  <code>sudo -i -u PROJECT_NAME</code>
* In the server (terminal),  <code>ALTER USER blog_analytics WITH PASSWORD 'myawesomepassword';</code>

## Setup Postgres
* In the server (terminal),  <code>touch local_settings.py</code>
* In the server (terminal),  <code>nano local_settings.py</code>
* In the server (terminal):
```
import os
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'PROJECT_NAME',
        'HOST': 'localhost',
        'USER': 'PROJECT_NAME',
        'PASSWORD': 'myawesomepassword'
    }
}

BASE_DIR = os.path.dirname(os.path.dirname(__file__))
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
STATIC_URL = '/static/'
```

## Setup Packages
* In the server (terminal),  <code>pip install -r requirements.txt</code>
* In the server (terminal),  <code>python manage.py makemigrations</code>
* In the server (terminal),  <code>python manage.py migrate</code>
* In the server (terminal),  <code>python manage.py collectstatic</code>

## Setup Gunicorn
* In the server (terminal),  <code>pip install gunicorn</code>
* In the server (terminal),  <code>touch PROJECT_NAME/gunicorn.conf.py</code>
* In the server (terminal),  <code>nano PROJECT_NAME/gunicorn.conf.py</code>
```
proc_name = "PROJECT_NAME"
bind = '127.0.0.1:8001'
loglevel = "error"
workers = 2
```

## Setup Supervisor
* In the server (terminal),  <code>sudo apt-get install supervisor</code>
* In the server (terminal),  <code>sudo service supervisor restart</code>
* In the server (terminal),  <code>sudo touch /etc/supervisor/conf.d/PROJECTS_NAME.conf</code>
* In the server (terminal),  <code>sudo nano /etc/supervisor/conf.d/PROJECTS_NAME.conf</code>
```
[group:PROJECT_NAME]
programs=gunicorn_PROJECT_NAME

[program:gunicorn_PROJECT_NAME]
command=/home/ubuntu/.virtualenvs/PROJECT_NAME/bin/gunicorn -c gunicorn.conf.py -p gunicorn.pid wsgi:application --pythonpath /home/ubuntu/PROJECT_NAME/PROJECT_NAME
directory=/home/ubuntu/PROJECT_NAME
user=ubuntu
autostart=true
autorestart=true
redirect_stderr=true
```

## Setup Nginx
* In the server (terminal),  <code>sudo touch /etc/nginx/sites-available/PROJECT_NAME.conf</code>
* In the server (terminal),  <code>sudo nano /etc/nginx/sites-available/PROJECT_NAME.conf</code>
```
server {
    server_name your_ec2_url;

    access_log off;

    location /static/ {
        alias /home/ubuntu/static/;
    }

    location / {
        proxy_pass http://127.0.0.1:8001;
        proxy_set_header X-Forwarded-Host $server_name;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header Host $host;
    }
}
```
* In the server (terminal),  <code>sudo ln -s /etc/nginx/sites-available/PROJECT_NAME.conf /etc/nginx/sites-enabled/PROJECT_NAME.conf</code>
* In the server (terminal),  <code>sudo rm /etc/nginx/sites-enabled/default</code>
* In the server (terminal),  <code>sudo service nginx restart</code>

## Setup Nginx
* In the server (terminal),  <code>nano local_settings.py</code>
* In local settings, set <code>DEBUG = False</code>
* In local settings, set <code>ALLOWED_HOSTS = ['your_ec2_url']</code>
* In local settings, set <code>sudo service supervisor restart</code>
* In local settings, set <code>sudo service nginx restart</code>
