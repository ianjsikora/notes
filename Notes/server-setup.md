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
