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
 * Edit the location of the website from <code>root /usr/share/nginx/html;</code> to <code>root /home/ubuntu/rocketu-portfolio;</code>
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
* In the server (terminal),
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




